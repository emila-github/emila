---
title: jquery - jquery each函数 break和continue功能
date: 2016-09-02 20:42:05
tags: [jquery]
---

## jquery - jquery each函数 break和continue功能 ##

	$('.container').each(function(i){
	     if($(this).attr('name')=="continue"){
	          return ;//实现continue功能
	     }else if($(this).attr('name')=="break"){
	          return false;//实现break功能
	     }
	});