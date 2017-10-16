---
layout: post
title:  "Django Web API拟稿readme.md"
tags: 后端
categories: 后端
---
# ORM

## Overview

I have repeated myself too many times and I don't want do that any more.

## Usage

```python
resources = Resources()
resources.add(name='users', User.objects.all())
resources.add(name='blogs', Blog.objects.all())

urlpatterns = [
    url(r'^', include(resources.urls)),
    url(r'^api-auth/', include('rest_framework.urls', namespace='rest_framework'))]
```

## Feature

- Automatically generates API.
- Automatically generates API Documentation.
- Automatically generates API Tests.