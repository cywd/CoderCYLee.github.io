---
layout: post
title: "QuartzCore/CATransformLayer.h"
excerpt: "QuartzCore/CATransformLayer.h"
categories: [OC, QuartzCore]
tags: [OC, QuartzCore]
date: 2016-04-14  
modified: 
comments: true
---

* TOC
{:toc}
---

用于创建真正的3D层层次结构。

CATransformLayer与CALayer有着细微的差别,但这些差别会影响到3D变换的动画效果.

详细可以看这篇文章 [详解CATransformLayer](https://www.cnblogs.com/YouXianMing/p/3777778.html)

```objective-c
/* CoreAnimation - CATransformLayer.h

   Copyright (c) 2006-2016, Apple Inc.
   All rights reserved. */

#import <QuartzCore/CALayer.h>

NS_ASSUME_NONNULL_BEGIN

/* "Transform" layers are used to create true 3D layer hierarchies.
 *
 * Unlike normal layers, transform layers do not project (i.e. flatten)
 * their sublayers into the plane at Z=0. However due to this neither
 * do they support many features of the 2D compositing model:
 *
 * - only their sublayers are rendered (i.e. no background, contents,
 *   border)
 *
 * - filters, backgroundFilters, compositingFilter, mask, masksToBounds
 *   and shadow related properties are ignored (they all assume 2D
 *   image processing of the projected layer)
 *
 * - opacity is applied to each sublayer individually, i.e. the transform
 *   layer does not form a compositing group.
 *
 * Also, the -hitTest: method should never be called on transform
 * layers (they do not have a 2D coordinate space into which to map the
 * supplied point.) CALayer will pass over transform layers directly to
 * their sublayers, applying the effects of the transform layer's
 * geometry when hit-testing each sublayer. */

CA_CLASS_AVAILABLE (10.6, 3.0, 9.0, 2.0)
@interface CATransformLayer : CALayer
@end

NS_ASSUME_NONNULL_END

```

