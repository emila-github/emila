---
title: gem 源更换
date: 2016-09-02 20:42:05
tags: [gem]
---
# gem 源更换 #

我们在使用gem更新的时候，经常会为速度抓狂，其实gem默认的源是https://rubygems.org，比较慢众所周至的原因了。
可以将源更换到国内的taobao源

## 查看当前有的源 ##

    gem sources -l

## 移除https://rubygems.org源 ##

    gem sources --remove https://rubygems.org/

## 增加http://ruby.taobao.org/源 ##

    gem sources -a http://ruby.taobao.org/

添加完用`gem sources -l`再查看一下，请确保只有http://ruby.taobao.org/这一个

## 查看当前 gem 环境 ##

    gem environment
