---
layout: post
title: "QuartzCore/CAMediaTimingFunction.h"
excerpt: "QuartzCore/CAMediaTimingFunction.h"
categories: [OC, QuartzCore]
tags: [OC, QuartzCore]
date: 2016-04-12  
modified: 
comments: true
---

* TOC
{:toc}
---

控制动画的节奏。可以使用系统提供的，也可以自定义。

```objective-c
/* CoreAnimation - CAMediaTimingFunction.h

   Copyright (c) 2006-2016, Apple Inc.
   All rights reserved. */

#import <QuartzCore/CAMediaTiming.h>
#import <Foundation/NSObject.h>

@class NSArray, NSString;

NS_ASSUME_NONNULL_BEGIN

/* Represents one segment of a function describing a timing curve. The
 * function maps an input time normalized to the range [0,1] to an
 * output time also in the range [0,1]. E.g. these functions are used
 * to define the pacing of an animation over its duration (or over the
 * duration of one keyframe). */

CA_CLASS_AVAILABLE (10.5, 2.0, 9.0, 2.0)
@interface CAMediaTimingFunction : NSObject <NSCoding>
{
@private
  struct CAMediaTimingFunctionPrivate *_priv;
}

// 可以通过以下方法去自定义

/* A convenience method for creating common timing functions. The
 * currently supported names are `linear', `easeIn', `easeOut' and
 * `easeInEaseOut' and `default' (the curve used by implicit animations
 * created by Core Animation). */

+ (instancetype)functionWithName:(NSString *)name;

/* Creates a timing function modelled on a cubic Bezier curve. The end
 * points of the curve are at (0,0) and (1,1), the two points 'c1' and
 * 'c2' defined by the class instance are the control points. Thus the
 * points defining the Bezier curve are: '[(0,0), c1, c2, (1,1)]' */

+ (instancetype)functionWithControlPoints:(float)c1x :(float)c1y :(float)c2x :(float)c2y;

- (instancetype)initWithControlPoints:(float)c1x :(float)c1y :(float)c2x :(float)c2y;

/* 'idx' is a value from 0 to 3 inclusive. */

- (void)getControlPointAtIndex:(size_t)idx values:(float[2])ptr;

@end

// 系统提供的，当然也可以自定义
/** Timing function names. **/
// 匀速，线性
CA_EXTERN NSString * const kCAMediaTimingFunctionLinear
    CA_AVAILABLE_STARTING (10.5, 2.0, 9.0, 2.0);
// 慢进快出，渐进
CA_EXTERN NSString * const kCAMediaTimingFunctionEaseIn
    CA_AVAILABLE_STARTING (10.5, 2.0, 9.0, 2.0);
// 快进慢出，渐出
CA_EXTERN NSString * const kCAMediaTimingFunctionEaseOut
    CA_AVAILABLE_STARTING (10.5, 2.0, 9.0, 2.0);
// 慢进慢出，中间加速，渐进渐出。这个是默认的动画行为。
CA_EXTERN NSString * const kCAMediaTimingFunctionEaseInEaseOut
    CA_AVAILABLE_STARTING (10.5, 2.0, 9.0, 2.0);
// 默认  kCAMediaTimingFunctionEaseInEaseOut
CA_EXTERN NSString * const kCAMediaTimingFunctionDefault
    CA_AVAILABLE_STARTING (10.6, 3.0, 9.0, 2.0);

NS_ASSUME_NONNULL_END

```

