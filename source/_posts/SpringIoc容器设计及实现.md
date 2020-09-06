---
title: SpringIoc容器设计及实现
date: 2020-08-31 12:39:56
tags: 
    - spring 
    - SpringIoc 
    - java
categories: spring
keywords: spring
cover: https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg.png
---

{% note primary no-icon %}
spring 的核心理念是Ioc(控制反转)和AOP(面向切面编程)
{% endnote %}

### 一、springIoc容器的设计

#### 1.容器的设计
{% note primary no-icon %}
    （1）BeanFactory
    ​（2）ApplicationContext(BeanFactory的子接口)
{% endnote %}

​	

#### 2.容器的初始化和依赖注入

Bean定义到IoC容器中3种方式
{% note primary no-icon %}
​	（1）Resourse定位	资源定位，常使用注解方式
​	（2）BeanDefinition载入
​	（3）BeanDefinition注册
{% endnote %}

#### 3.SpringBean的周期

从容器初始化到销毁的过程

### 二、装配SpringBean

#### 1.	3种装备方式
{% note primary no-icon %}
​	（1）构造器注入
​	（2）setter注入（主流方式）
​	（3）接口注入
{% endnote %}





​	


