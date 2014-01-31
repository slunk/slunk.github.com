---
layout: post
title: "BST from Array"
description: ""
category: 
tags: ["binary search trees", "arrays", "binary search"]
prompt: "Given a binary search tree, design an algorithm which creates a linked list of all the nodes at each depth (i.e., if you have a tree with depth D, you’ll have D linked lists)."
time: "12 minutes"
code_time: "Unavailable"
gist: "https://gist.github.com/slunk/8734353"
---
{% include JB/setup %}
Approach: Given the highest and lowest elements in the array you're allowed to touch, construct the BST nodes recursively.
The value in the node one function call is responsible for constructing is the element in the array at the midpoint between the lowest and highest elements.
This is very similar to performing a binary search on the array.

Original python-like pseudocode:

    def make_tree(arr, lo, hi):
        if (lo != 0 && lo < hi - 1) or lo < hi: # This is incorrect
            return None
        mid = (lo + hi) / 2
        return Tree(arr[mid], make_tree(arr, lo, mid), make_tree(arr, mid, hi))

This wasn't functional, but the basic idea was there.

## Lessons

1. Don't practice when I'm sleepy. It's a waste of time.
