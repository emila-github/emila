---
title: DataTables - Jquery DataTables 基本设置
date: 2016-09-02 20:42:05
tags: [jquery,DataTables]
---

DataTables - Jquery DataTables 基本设置
	
	
	$('#example').dataTable({  
		   "sScrollX": "100%", //表格的宽度   
		   "sScrollXInner": "110%", //表格的内容宽度
		   "bScrollCollapse": true, //当显示的数据不足以支撑表格的默认的高度时，依然显示纵向的滚动条。(默认是false)  
	       "bPaginate": true,  //是否显示分页  
	       "bLengthChange": true,  //每行显示的记录数  
	       "bFilter": true, //搜索栏  
	       "bSort": true, //是否支持排序功能  
	       "bInfo": true, //显示表格信息  
	       "bAutoWidth": false,  //自适应宽度  
	       "aaSorting": [[1, "asc"]],  //给列表排序 ，第一个参数表示数组 (由0开始)。1 表示Browser列。第二个参数为 desc或是asc  
	       "aoColumns": [  
	           null,  
	           null,  
	           {   
	               "bVisible": true, //不可见  
	               "bSearchable": false, //参与搜索  
	           },  
	           null,  
	           null  
	       ], //列设置，表有几列，数组就有几项  
	        "bStateSave": true, //保存状态到cookie *************** 很重要 ， 当搜索的时候页面一刷新会导致搜索的消失。使用这个属性就可避免了  
	       "sPaginationType": "full_numbers", //分页，一共两种样式，full_numbers和two_button(默认)  
	       "oLanguage": {  
	           "sLengthMenu": "每页显示 _MENU_ 条记录",  
	           "sZeroRecords": "对不起，查询不到任何相关数据",  
	           "sInfo": "当前显示 _START_ 到 _END_ 条，共 _TOTAL_ 条记录",  
	           "sInfoEmtpy": "找不到相关数据",  
	           "sInfoFiltered": "数据表中共为 _MAX_ 条记录)",  
	           "sProcessing": "正在加载中...",  
	           "sSearch": "搜索",  
	           "sUrl": "", //多语言配置文件，可将oLanguage的设置放在一个txt文件中，例：Javascript/datatable/dtCH.txt  
	           "oPaginate": {  
	               "sFirst":    "第一页",  
	               "sPrevious": " 上一页 ",  
	               "sNext":     " 下一页 ",  
	               "sLast":     " 最后一页 "  
	           }  
	       }, //多语言配置  
	       "bJQueryUI": false, //可以添加 jqury的ui theme  需要添加css  
		   "aLengthMenu": [[10, 25, 50, -1, 0], ["每页10条", "每页25条", "每页50条", "显示所有数据", "不显示数据"]] //设置每页显示记录的下拉菜单
	   });  
	}); 