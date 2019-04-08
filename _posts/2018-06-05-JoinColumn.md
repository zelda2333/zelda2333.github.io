---
layout: post
title: JoinColumn注释
---
用法实例:
@ManyToOne(targetEntity = Staff.class)
@JoinColumn(name = "auditedStaffId", referencedColumnName = "staffId")
private Staff auditedStaff;// 审核人
ManyToOne指的是多对一的数据关系,many指的是本类.one指的是目标类.
targetEntity 指的是目标类,即要加入到本类的实体类
referencedColumnName 指的是以目标类的何种属性作为本类的外键,不设置的话默认是目标类的主键.
name 指的是目标类外键在本类存的名称,例如目标类的外键是staffId,他在目标类的列名是staffId,在本类的列名是auditedStaffId.
再说一下jsp的传值,页面name的属性直接设置为 auditedStaff点上Staff类里本身的属性.和以上的设置无关.



JAVA读取本地文件并显示到页面中
https://blog.csdn.net/huozengguang/article/details/53098122