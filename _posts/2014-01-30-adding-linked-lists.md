---
layout: post
title: "Adding Linked Lists"
description: ""
category: 
tags: ["linked lists"]
prompt: "You have two numbers represented by a linked list, where each node contains a single digit. The digits are stored in reverse order, such that the 1’s digit is at the head of the list. Write a function that adds the two numbers and returns the sum as a linked list. EXAMPLE Input: (3 -> 1 -> 5) + (5 -> 9 -> 2) Output: 8 -> 0 -> 8"
time: "10 minutes"
code_time: "10 minutes"
gist: "https://gist.github.com/slunk/8725994"
---
{% include JB/setup %}
Approach iterate through both lists at once.
Sum the digits with a carry and add the result mod 10 to a new list.
Do some extra work afterwards if there are more elements in one of the input lists, or a final carry.

Original c-like pseudocode:

    while (one != NULL && two != NULL) {
        sum = one->val + two->val + carry;
        rval->add(sum % 10)
        if (sum >= 10) {
            carry = 1;
        } else {
            carry = 0;
        }
        one = one->next;
        two = two->next;
    }
    if (one == NULL)
        one = two;
    for (; one != NULL; one = one->next) {
        rval->add(one->val + carry);
        carry = 0;
    }
    if (carry)
        rval->add(carry);
