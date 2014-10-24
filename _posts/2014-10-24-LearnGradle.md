---
layout: post
title:  "学习Gradle文件的写法"
date:   2014-10-24 10:22:54
categories: random
---

Android开发，使用Android Studio的时候，会在项目目录下边有*.gradle文件。

### settings.gradle的作用

1.配置项目工程目录和子项目的目录，其中目录用":"隔开

例如：```include ':app', ':extras:Utils'```
表示将该目录下的app目录和extras目录下的Utils目录添加为项目

### build.gradle的作用

1.build.gradle一般放到项目根目录或者子项目（sub-projects）或子模块（modules）中，用来分别配置整合项目和模块的规则。

2.根目录下的build.gradle用来描述这个项目的整体构建基础

buildscript{}

环境配置

repositories{}

基本固定写法，mavenCentral

dependencies{}

依赖配置

apply plugin:

    java/android/android-library

android{}

Android的一些配置，支持版本等

signingConfigs{}

签名相关

productFlavors{}

多渠道打包相关

### DSL(Domain Specific Language)

特定领域语言，是一种为了特定任务而设计的开发语言