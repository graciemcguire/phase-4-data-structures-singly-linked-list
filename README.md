# Singly Linked List Data Structure

## Learning Goals

- Identify the use cases for a `Linked List`
- Demonstrate common methods for a `Linked List`
- Differentiate between a `Singly Linked List` and a `Doubly Linked List`

## Introduction

In this lesson, we'll learn what a `Linked List` is, along  with how to build and implement one in a class along with some of
its common methods to get an understanding of what the differences between a `Singly Linked List` and a `Doubly Linked List` are.

## Why Linked Lists?

We  use linked lists bc they take less insertion time when we have  a  lot of data. Think about if we have a sorted alphabet array of 10 elements representing letters.

```rb
[  "A", "B", "C", "D", "E", "F", "H", "I", "J", "K" ]
   [0]  [1]  [2]  [3]  [4]  [5]  [6]  [7]  [8]  [9]
```rb

After creating our array, we realize we forgot one letter in our array! If we added the letter "G" to the end of the array, it would no longer be sorted, so we would need  to  _insert_ the "G" element into the array in the correct index, which would be  6. Because there  is already  an element in the 6th index, and more elements in the sequential indexes, all of those elements would have  to be  shifted down a  spot,  and given a new index. Because this is a smaller array  it doesn't seem like the biggest deal to move the last 4 elements down a place, but as  you  can imagine, if we had an array  of 100s or thousands or even millions of elements, re indexing *all* of those elements would take a really long time! This is where linked lists come in handy! 