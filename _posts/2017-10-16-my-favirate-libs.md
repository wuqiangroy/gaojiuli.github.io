---
layout: post
title:  "关于RESTful接口"
tags: Python
categories: 后端
---
# RESTful

> 一种软件架构风格，设计风格而不是标准，只是提供了一组设计原则和约束条件。它主要用于客户端和服务器交互类的软件。基于这个风格设计的软件可以更简洁，更有层次，更易于实现缓存等机制。

## Model

使用ORM对数据库进行映射以方便操作，如Django ORM

```python
class User(Model):
    username = CharField(max_length=255)
    password = CharField(max_length=255)
    is_active = BoolField(default=true)

class Blog(Model):
    title = CharField(max_length=255)
    content = TextField()
    author = ForeignKey(User)
```

## Resource

理想情况下，定义好Resource那么相应的API应该自动暴露出来。

```python
class BlogResource(Resouce):
    extra = CharField(default='extra_string')
    class Meta:
        model = Blog
        api = 'blogs'
```

以上将自动生成API接口

```shell
GET     /blogs/
GET     /blogs/:id
POST    /blogs/
DELETE  /blogs/:id
PUT     /blogs/:id
PATCH   /blogs/:id
```

权限过滤

```python
class BlogResource(Resouce):
    extra = CharField(default='extra_string')
    class Meta:
        model = Blog
        api = 'blogs'
        permissions = {
            'list': 'list_blog',
            'retrieve': 'retrieve_blog',
            'create': 'create_blog',
            'update': 'update_blog',
            'update_{field}': 'update_blog_{field}',
            'update_{field}_to_{value}': 'update_blog_{field}_to_{value}',
            'delete': 'delete_blog'
        }
```

关联变化

```python
class BlogResource(Resouce):
    extra = CharField(default='extra_string')
    class Meta:
        model = Blog
        api = 'blogs'
        ralations = {
            'on_list': None,
            'on_retrieve': None,
            'on_create': [update('author',{'is_active': true}),],
            'on_update': None,
            'on_update_{field}': None,
            'on_update_{field}_to_{value}': None,
            'on_delete': None
        }
```