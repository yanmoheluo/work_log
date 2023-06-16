[[02-obsidian模板]]
新加笔记 ctrl +N
obsidian内容同步
obsidian命令面板
obsidian快捷键
obsidian搜索技巧

入链      shift +6
出链
创建别名   shift+\

引用段落!+名字 
引用标题#+
引用段落


#双链的意义
	* 线性笔记vs知识网络
	* 回顾：obsidian擅长的事情
	* 管理知识片段
* ob带来的新思维
* 基于方法使用工具
* 基于思维提炼方法
* 链接->管理思维
* 片段->整合思维
搜索技巧
	·直接搜索关键词
	搜索包含多个关键词的文档(空格间隔)
	搜索包含某一个关键词的文档 (OR)
	指定搜索范围
		搜索文件名 file.word
		搜索文本内容 contentword
		搜索标签 tag:\tag.word
		搜索同一行中的多个关键词 line:word1 word2
		搜索同一章节中的多个关键词 section:word1 word2搜索同一段落 (块)中的多个关键词 block:word1
		word2
搜索任务

搜索任务 task:""
搜索未完成任务 task-todo:""
搜索已完成任务 task-done:""

保存查询结果
代码 query
```query

```

dataview 搜索查询


数据库
Obsidian资料库 =一个数据库
学习方式:
掌握原理和语法
使用时查阅该文档
Dataview
咱普通人最接近数据库的一次定义: Obsidian资料库的查询工具/插件
查询对象: Obsidian数据库
查询依据:YAML数据/Meatainfo场景
什么时候使用搜索
条件单一
无需保存结果
什么时候使用查询
条件复杂
需要保存结果
YAML 


Obsidian文件属性
file.name: 文件标题(字符串)
file.folder: 文件所属文件夹路径
file.path: 文件路径
file.size: (in bytes) 文件大小
file.ctime: 文件的创建时间 (包含日期和时间)
file.mtime: 文件的修改时间
file.cday: 文件创建的日期
file.mday: 文件修改的日期
file.tags: 笔记中所有标签数组file.etags: 除去子标签的数组file.inlinks: 指向此文件的所有传入链接的数组file.outlinks: 此文件所有出站的链接数组
file.aliases: 文件别名数组
file.day: 如果文件名中有日期，那么会以这个字段显示。比如文件名中包含 yyyy-mm-dd (年-月-日，例如2021-03-21)，那么就会存在这个 metadata
dataview[listltableltask] field1, field2 as myfield,from #tag or "folder" or [[link]] or outgoing([[link]])field [>|>=<l<=]=]&]''] [field2lliteral value] (and field2 ...) (or field3...)wheresortfield (ascendingldescendinglascldesc] (ascending is implied if not provided)
Metainfo
Title:10.公开课总结
Author:Sandox
Date:2022-08-09 周二
Tags:
#课程
#工具

精细化的整理
标签
链接
metainfo
索引
4.注意事项
狠抓核心功能，插件锦上添花
Obsidian从入门到放弃
折腾汉化
折腾主题
折腾插件
别用于收集
逻辑比功能更重要
同步
iOs没有最优解
你真的需要同步手机吗?强大与易用不可兼得字体、颜色，如何修改?
无解的问题
会者不问
问者不会