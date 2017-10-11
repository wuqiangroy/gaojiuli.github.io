---
layout: post
title:  "我的API开发规范"
tags: 后端
categories: 后端
---

> 想要缩短开发周期，提高开发效率，一套稳定可靠的规范是必不可少的。

## 请求方法

```python
"""
列表		GET         /resources/
详情		GET         /resources/:id/
创建		POST        /resources/:id/
替换		PUT         /resources/:id/
更新		PATCH       /resources/:id/
删除		DELETE      /resources/:id/
选项		OPTIONS     /resources/:id/
"""
```

## 分页过滤

```python
"""
GET /resources/:id/?limit={数量}&
                    offset={偏移量}&
                    search={查询关键词}&
                    condition1={过滤条件1}&
                    condition2={过滤条件2}&
                    fields=返回字段1,返回字段2
"""
```



## 数据传输

```python
普通数据	"application/json",
文件上传	"multipart/form-data"
```

## 时间格式

```python
规范		"ISO 8601"
结构		"YYYY-MM-DDTHH:MM:SSZ"
案例		"2017-09-05T08:23:51.464177Z"
```

## 身份认证

```python
软件		"Authorization: token :TOKEN"
网页		"Cookie"
```

## 返回状态

```python
"""
200	请求成功
201	创建成功
400	参数错误
401	未登录
403	无权限
404	未找到
50X	服务器错误
"""
```

## 后端依赖

```
django
djangorestframework
django-url-filter
django-redis
celery
postgresql
```

## 后端部署

```
Ubuntu Server
Nginx  <----> uWSGI <----> Django <----> Redis、PostgreSQL
```

