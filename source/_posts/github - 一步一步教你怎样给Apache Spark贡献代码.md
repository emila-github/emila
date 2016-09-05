---
title: github - 一步一步教你怎样给Apache Spark贡献代码
date: 2016-09-02 20:42:05
tags: [git]
---
# github - 一步一步教你怎样给Apache Spark贡献代码 #

**本文将教大家怎样用10个步骤完成给Apache Spark贡献代码这个任务：）**

## 到 Apache Spark 的github 页面内点击 fork 按钮 ##


## 你的github帐户中会出现 spark 这个项目 ##


## 本地电脑上， 使用 ##
	git clone [你的 spark repository 的 github 地址]
	例如：
	git clone git@github.com:gchen/spark.git

本地得到一个叫 spark 的文件夹

## 进入该文件夹，使用 ##

	git remote add upstream https://github.com/apache/spark.git

添加 Apache/spark 的远程地址
## 使用 ##
	git pull upstream master

得到目前的 Apache/spark 的最新代码，现在我们在 你自己fork的Spark代码仓库的master 这个分支上，以后这个分支就留作跟踪 upstream 的远程代码


## 好了，现在你可以开始贡献自己的代码了。 ##
按照开发惯例，我们一般不在自己代码仓库的master上提交新的代码，而是需要为每一个新增的功能或者bugfix新增一个新的branch。使用：

    git checkout -b my_change

创建新的分支，现在我们可以在这个分支上更改代码

## 添加代码，并提交代码： ##
	$ git add .
	$ git commit -m “message need to be added here”

## 提交Pull Request前合并冲突 ##

在我们提交完我们的代码更新之后，一个常见的问题是远程的upstream（即apache/spark)已经有了新的更新，从而会导致我们提交Pull Request时会导致conflict。为此我们可以在提交自己这段代码前手动先把远程其他开发者的commit与我们的commit合并。使用：

	git checkout master

切换到我们自己的主分支，使用
	git pull upstream master

拉出apache spark的最新的代码。切换回 my_change 分支，使用

	git checkout my_change
	git rebase master

然后把自己在my_change分支中的代码更新到在自己github代码仓库的my_change分支中去：
	git push origin my_change 

将代码提交到自己的仓库。

## 提交Pull Request ##


这时候可以在自己的仓库页面跳转到自己的my_change分支，然后点击 new pull request。按照Spark的风格规定，我们需要在新的Pull Request的标题最前面加上JIRA代号。所以我们需要在[https://issues.apache.org/jira/](https://issues.apache.org/jira/)上创建一个新的JIRA，例如[https://issues.apache.org/jira/browse/SPARK-2859](https://issues.apache.org/jira/browse/SPARK-2859)。然后把SPARK-2859这个代号加到你的Pull Request的标题里面。

例如：[https://github.com/apache/spark/pull/1782](https://github.com/apache/spark/pull/1782)

**Pull Rquest的描述的写法很重要。有几个要点：**

1. 在Pull Request的描述中，一定记得加上你提交的JIRA的url，方便JIRA系统自动把Pull Request的链接加进去，例如https://issues.apache.org/jira/browse/SPARK-2859。

1. PR的描述要言简意赅，讲清楚你要解决的问题是什么，你怎么解决的。大家可以多参考其他committer提交的PR。

## 等待Spark committer审核你的PR。 ##

如果需要进一步的代码修改，你可以继续在本地的my_change分支下commit新的代码，所有新的代码会在”git push origin my_change”之后自动被加入你之前提交的Pull Request中，方便进行问题的跟踪和讨论。

## 如果一切顺利，具有apache/spark.git 写权限的commiter就会把你的代码merge到apache/spark.git的master里面去了！ ##

恭喜你！相信你一定很开心吧？

Happy contributing to Spark!

ps. 你的代码被merge完之后，就可以把my_change这个分支给删掉了:)

注：本文写的比较仓促，是在@[lufeihaidao](https://github.com/lufeihaidao) 的基础上直接修改而成，特此感谢：[https://github.com/19wu/19wu/issues/41](https://github.com/19wu/19wu/issues/41)

## 参考： ##

- [一步一步教你怎样给Apache Spark贡献代码](http://www.geekbus.cn/step-to-step-to-contribute-spark-repository/)
- [How to use github pull request](https://help.github.com/articles/using-pull-requests)
- [github的多人协作](https://gist.github.com/suziewong/4378619)
- [How to rebase a pull request](https://github.com/edx/edx-platform/wiki/How-to-Rebase-a-Pull-Request)
- [我提交的一个JIRA例子](https://issues.apache.org/jira/browse/SPARK-2859)
- [我提交的一个Spark PR的例子](https://github.com/apache/spark/pull/1782)