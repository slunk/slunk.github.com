---
layout: post
title: "All Subsets"
description: ""
category: 
tags: ["recursion", "sets"]
prompt: "Write a method that returns all subsets of a set."
time: "11 minutes"
code_time: "6 minutes"
gist: "https://gist.github.com/slunk/8702106"
---
{% include JB/setup %}
Approach: If you have a set S = {a, b, c}, subsets(S) = {a} U subsets({b, c}) and subsets({b, c}).
The only subset of the empty set is itself.

Original python-like pseudocode:

    def subsets(s):
        if s.empty():
            return [{}]
        first = set(s.elts()[0])
        rest = s - first
        ssets = subsets(rest)
        return [first U set for set in ssets] + ssets


