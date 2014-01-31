---
layout: post
title: "Common Ancestor"
description: ""
category: 
tags: ["binary trees", "trees"]
prompt: "Design an algorithm and write code to find the first common ancestor of two nodes in a binary tree. Avoid storing additional nodes in a data structure. NOTE: This is not necessarily a binary search tree."
time: "9 minutes"
code_time: "16 minutes"
gist: "https://gist.github.com/slunk/8734427"
---
{% include JB/setup %}
Approach: Assign the lower node to its parent ndoe until both nodes are at the same depth, then assign both nodes to their parents until they are the same.

Original python-like pseudocode:

    def common_ancestor(a, b):
        while depth(a) < depth(b): # Note: there is an insidious error here.*
            a = a.parent
        while depth(b) < depth(b):
            b = b.parent
        while a != b:
            a = a.parent
            b = b.parent
        return a

* I was thinking about depth as a quantity that gets lower as you get lower in the tree, but it is basically always calculated as a positive integer.
I figured this out while I was programming, and it was a tricky logic error to catch.

## Lessons

1. Make sure to explicitely think about the return values of helper functions you haven't defined.
