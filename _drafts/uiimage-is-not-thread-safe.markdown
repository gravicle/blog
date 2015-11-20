---
title: UIImage is NOT thread safe
date: 2015-11-19 21:44:05 -0600
layout: post
summary: Using UIImage classes from threads other than the main thread can lead to obscure and hard to reproduce crashes, the worst kind.
---

Nick asked if it is safe to decide image data on another thread using `UIImage(data:)` initializer.

