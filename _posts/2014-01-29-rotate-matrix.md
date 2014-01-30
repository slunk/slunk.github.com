---
layout: post
title: "Rotate Matrix"
description: ""
category: 
tags: ["matrix"]
prompt: "Given an image represented by an NxN matrix, where each pixel in the image is 4 bytes, write a method to rotate the image by 90 degrees. Can you do this in place?"
time: "45 minutes"
code_time: "15 minutes"
gist: "https://gist.github.com/slunk/8702522"
---
{% include JB/setup %}
First approach: Iterate through every cell and copy it to the appropriate cell in a new matrix.

Original c-like pseudocode:

    for (i = 0; i < N; i ++) {
        for (j = 0; j < N; j++) {
            rot[N - 1 - j][i] = mat[i][j];
        }
    }

The real challenge is to do it in place, and it took me a while to figure out.
Cells rotate in groups of four.
Given a cell's location and the size of the matrix, you can determine the other three cells.
Known a full group, you can swap them using only 4 bytes of temporary storage.

Original c-like pseudocode:

    for (i = 0; i < n / 2; i++) {
        for (j = i; i < n - 1 - i; j++) {
            swap_left(&mat[i][j], &mat[j][n - 1 - i], &mat[n - 1 - i][n - 1 - j], &mat[n - 1 - j][i])
        }
    }

    void swap_left(a, b, c, d) {
        tmp = *a
        *a = *b
        *b = *c
        *c = *d
        *d = tmp
    }
