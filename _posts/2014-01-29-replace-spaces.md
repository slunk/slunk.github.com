---
layout: post
title: "Replace spaces"
description: ""
category: 
tags: ["strings"]
prompt: "Write a method to replace all spaces in a string with ‘%20’."
time: "5 minutes"
code_time: "6 minutes"
gist: "https://gist.github.com/slunk/8702310"
---
{% include JB/setup %}
Approach: Count the number of spaces in a first pass, allocate room for a new string, and copy everything except the spaces.

Original c-like pseudocode:

    for (i = 0; i < strlen(s); i++) {
        if (s[i] == ' ')
            space_count++;
    }

    rval = malloc(strlen(s) + 2 * space_count)
    j = 0

    for (i = 0; i < strlen(s); i++) {
        if (s[i] == ' ') {
            rval[j++] = '%';
            rval[j++] = '2';
            rval[j++] = '0';
        } else {
            rval[j++] = s[i]
        }
    }
