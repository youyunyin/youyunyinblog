---
title: Java原生实现分页方案
categories: java
tags: [java]
date: 2015-05-29
---

# 两种分页方式
1. 截取lisit
2. 生成特定分页sql（不同数据库分页sql不同）

# 方案一 截取list
截取list，针对后台查询出来的list数据，前台传入当前页currentPage，每页记录数numPerPage,从而计算出当前页的起始和终止下标，截取list返回前台。

实现：
* PaginationInfo 分页信息对象
* PaginationUtil 分页工具类，传入原始全量list，根据前台传入的页码每页数据量进行截取

如下关键代码

```java
if("pagedemo".equals(action)){
//每页显示数据条数
	int numPerPage = 5;
	//要显示的页
int currentPage = Integer.parseInt((String)request.getParameter("currentPage"));
	StringBuffer json = new StringBuffer();
	List<UserVO> list = new ArrayList<UserVO>();
	try {
		//要显示的所有数据
		list = userMngService.queryAllUser();
		//第一种分页方式，先取所有list，然后截取list分页
		PaginationUtil<UserVO> paginationUtil = new PaginationUtil<UserVO>();
		PaginationInfo<UserVO> paginationInfo = paginationUtil.listDataProcess(list, numPerPage, currentPage);
		//要显示的数据
		list = paginationInfo.getResultList();
		json.append(" {\"total\":");
		//数据总数
		json.append(paginationInfo.getTotalPages());
		json.append(",\"rows\":[  ");
		for(int i = 0;i<list.size();i++){

		 . . . . . . 
}
```
步骤：
1. 获取前台传参数当前页currentPage,
2. 设置分页规则：每页记录数
3. 获取要显示的所有数据信息list
4. 使用工具类PaginationUtil截取list。返回PaginationInfo对象

PaginationInfo对象中包含了结果relustList
页码，总记录数等信息，根据需要取得数据返回json到前台。

# 方案二 特定分页sql

![](/images/java分页类图.png)

在需要进行分页处理的DMO类中使用JdbcPaginationDelegator代理类处理，使用PaginationInfo对象存储数据信息。结果list，总页数等
示例:
```java
/**
	 * 查询所有用户信息 分页
	 * @param currentPage	当前页
	 * @param numPerPage	每页显示数据条数
	 * @return
	 */
	Public PaginationInfo<UserVO> queryUserByPageInfo(int currentPage,int numPerPage){
    。。。。
  }
```
**步骤：**
1. 创建基本查询sql
```java
	StringBuffer sql = new StringBuffer();
	sql.append("select * from ump_user where dr = ?");
```
2. 创建分页信息对象，分页工具代理，如需sql参数创建sql参数对象SQLParameter，如果没有则传null
```java
//分页信息
PaginationInfo<UserVO> pagenationInfo = new PaginationInfo<UserVO>();
//jdbc分页代理对象
JdbcPaginationDelegator<UserVO> delegate = new JdbcPaginationDelegator<UserVO>();
//sql参数信息
SQLParameter param = new SQLParameter();
param.addParam(0);
```
3. 使用代理对象初始化分页信息
```java
//使用代理对象初始化分页信息，代理类中会计算总记录数，但是不会执行分页sql，因为很多没有使用元数据没有，vo和数据表的映射
//所以没法自动的将rs生成vo，所以，代理只是生成分页特定数据库的分页sql语句，由调用对象自行执行。
pagenationInfo = delegate.initPaginationInfo(sql.toString(), param, currentPage, numPerPage);
```
4. 执行代理类生成的分页SQL
```java
//执行代理类生成的分页查询sql
stmt = conn.prepareStatement(paginationInfo.getPageSql());
stmt.setInt(1, 0);
rs = stmt.executeQuery();
```

# 两种方式对比：

两种方案的优劣比较明显，截取list每次都要全查出来，如果list的数据量非常大每次全查耗时较多，可考虑方案二，但是，此方案改动的代码量少，只需要在action加几行代码处理即可。

使用分页sql，方案效率较高，每次只取需要的数据，劣势在于需更改的代码较多，同时如果涉及到多次联查取综合数据的场景则此方案无效，只能使用方案一。