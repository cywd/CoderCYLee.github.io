---
layout: post
title: "objc/NSObjCRuntime.h"
excerpt: "objc/NSObjCRuntime.h"
categories: [OC]
tags: [Runtime, OC]
date: 2014-12-28 
modified: 
comments: true
---

* TOC
{:toc}
---

```c
/*	NSObjCRuntime.h
	Copyright (c) 1994-2012, Apple Inc. All rights reserved.
*/

#ifndef _OBJC_NSOBJCRUNTIME_H_
#define _OBJC_NSOBJCRUNTIME_H_

#include <TargetConditionals.h>
#include <objc/objc.h>

// 宏定义
#if __LP64__ || (TARGET_OS_EMBEDDED && !TARGET_OS_IPHONE) || TARGET_OS_WIN32 || NS_BUILD_32_LIKE_64
typedef long NSInteger;
typedef unsigned long NSUInteger;
#else
typedef int NSInteger;
typedef unsigned int NSUInteger;
#endif

// 宏定义
#define NSIntegerMax    LONG_MAX  // 最大长整形
#define NSIntegerMin    LONG_MIN  // 最小长整形
#define NSUIntegerMax   ULONG_MAX 

#define NSINTEGER_DEFINED 1

#ifndef NS_DESIGNATED_INITIALIZER
#if __has_attribute(objc_designated_initializer)
#define NS_DESIGNATED_INITIALIZER __attribute__((objc_designated_initializer))
#else
#define NS_DESIGNATED_INITIALIZER
#endif
#endif

#endif
```

