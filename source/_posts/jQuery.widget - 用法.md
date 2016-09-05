---
title: jQuery.widget - 用法
date: 2016-09-02 20:42:05
tags: [jquery, widget]
---
# jQuery.widget - 用法 #

jQuery UI 中包含许多保持状态的小部件，因此比典型的 jQuery 插件稍有不同的使用模式。所有的jQuery UI 小部件使用相同的模式，这是由部件库（Widget Factory）定义的。所以，只要您学会使用其中一个，您就知道如何使用其他的小部件（Widget）。



注释：本章节使用 进度条部件（Progressbar Widget） 演示实例，但是语法适用于每个小部件。


## 初始化 ##

为了跟踪小部件的状态，我们必须引入小部件的全生命周期。小部件初始化时生命周期开始。要初始化一个小部件，我们只需要简单地在一个或多个元素上调用插件。

    $( "#elem" ).progressbar();

这将初始化 jQuery 对象中的每个元素。上面实例中元素 id 为 "elem"。

## 选项 ##

由于 progressbar() 调用时不带参数，小部件是使用默认选项进行初始化的。我们可以在初始化时传递一组选项来覆盖默认选项：

    $( "#elem" ).progressbar({ value: 20 });

我们可以根据需要传递选项的个数，任何我们未传递的选项都使用它们的默认值。

您可以传递多个选项参数，这些参数将会被合并为一个对象（类似于 `$.extend( true, target, object1, objectN )`）。这在为所有实例覆盖一些设置，实例间共享选项时很有用：

	var options = { modal: true, show: "slow" };
	$( "#dialog1" ).dialog( options );
	$( "#dialog2" ).dialog( options, { autoOpen: false });

所有在初始化时传递的选项都是深拷贝的，确保后续在不影响小部件的情况下修改对象。数组是唯一的例外，它们是按原样引用的。这个例外是为了适当地支持数据绑定，其中数据源必须作为引用。

默认值保存在小部件的属性中，因此我们可以覆盖 jQuery UI 设置的值。例如，在下面的设置后，所有将来的进度条实例将默认为值 80：


	$.ui.progressbar.prototype.options.value = 80;

选项是小部件状态的组成部分，所以我们也可以在初始化后设置选项。我们会在后续看到 option 方法。

## 方法 ##

现在小部件已经初始化，我们可以查询它的状态，或者在小部件上执行动作。所有初始化后的动作都是以方法调用方式执行。为了在小部件上调用一个方法，我们向 jQuery 插件传递方法的名称。例如，在进度条部件（Progressbar Widget）上调用 value() 方法，我们可以使用：

	$( "#elem" ).progressbar( "value" );

如果方法接受参数，我们可以在方法名称后传递参数。例如，要传递参数 40 到 value() 方法，我们可以使用：

	$( "#elem" ).progressbar( "value", 40 );

就像 jQuery 中的其他方法，大多数的小部件方法返回 jQuery 对象：

	$( "#elem" )
	  .progressbar( "value", 90 )
	  .addClass( "almost-done" );

每个小部件都有自己的方法设置，这些设置是基于小部件提供的功能。但是，有一些方法是存在于所有的小部件上，这会在下面进行详细讲解。

## 事件 ##
所有的小部件都有与它们各种行为相关的事件，以便在状态改变的时候通知您。对于大多数的小部件，当事件被触发时，名称以小部件名称的**小写字母形式作为前缀**。例如，我们可以绑定进度条的 change 事件，该事件在值改变时触发。

	$( "#elem" ).bind( "progressbarchange", function() {
	  alert( "The value has changed!" );
	});

每个事件都有一个对应的回调，这会作为选项。如果需要，我们可以抓住进度条的 change 回调，而不用绑定 progressbarchange 事件。

	$( "#elem" ).progressbar({
	  change: function() {
	    alert( "The value has changed!" );
	  }
	});

所有的小部件都有一个 change 事件，该事件在实例化时触发。

## 实例化 ##

小部件的实例是使用带有小部件全称作为键的 `jQuery.data()` 存储的。因此，您可以使用下面代码从元素检索进度条部件（Progressbar Widget）的实例对象。

	$( "#elem" ).data( "ui-progressbar" );

**元素是否绑定了给定小部件**，可以使用 `:data` 选择器来检测。


	$( "#elem" ).is( ":data( 'ui-progressbar' )" ); // true
	$( "#elem" ).is( ":data( 'ui-draggable' )" ); // false


您也可以使用 :data 来获得作为给定小部件实例的所有元素的列表。

	$( ":data( 'ui-progressbar' )" );

## 实例销毁 ##

    if($( "#elem" ).data('ui-progressbar')) {//判断实例是否存在
        $( "#elem" ).progressbar('destroy');
    }
