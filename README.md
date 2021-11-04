# Singly Linked List Data Structure

## Learning Goals

- Identify the use cases for a Singly Linked List
- Demonstrate common methods for a Singly Linked List
- Differentiate between a Singly Linked List and an array

## Introduction

In this lesson, we'll learn what a **Singly Linked List** is, along with how to
build a `LinkedList` class. We'll also learn some of its common methods to get
an understanding of what the differences between a Singly Linked List and an
array are.

## What Is a Linked List?

A linked list is a linear (ordered) collection of data that consists of several
elements, called **nodes**, with each node pointing to the next node in the
list. Unlike arrays, linked lists aren't indexed.

Think of it like a train: each car is connected to the next car, which is
connected to the next car, and so forth. In an array, we can say "Give me the
sixth element," but in a linked list, we have to start at the beginning of the
train, and go from the first car, to the second car, and so forth:

The nodes in a linked list each have a value, and a pointer to another node,
otherwise pointing to nil if it is at the end of the list.

## Why Linked Lists?

Linked lists and arrays are both data structures that can hold ordered lists of
data. Depending on what kind of operations you need to perform with that list,
there are some scenarios where a linked list can be more efficient than an
array, such as efficiently adding and removing elements from any arbitrary
position within the list.

Think about if we have a sorted dog array of 5 elements representing
dog breeds:

```rb
["Bulldog", "Chihuahua", "German Shepard", "Retriever", "Shiba Inu"]
   [0]          [1]            [2]             [3]          [4] 
```

After creating our array, we realize we forgot to add one dog in our array, a
Chow Chow! To fix our array, we would need to _insert_ the "Chow Chow" element
into the array in the correct index, which would be 2. Because there is already
an element in the 2th index, and more elements in the sequential indexes, all of
those elements would have to be shifted down a spot, and given a new index.

![Pup Array](https://curriculum-content.s3.amazonaws.com/pup_array.png)

Since this is a smaller array, it doesn't seem like the biggest deal to move
the last 3 elements down a place, but as you can imagine, if we had an array of
hundreds or thousands or even millions of elements, reindexing _all_ of those
elements would take a really long time! This is where linked lists come in
handy.


## Defining a Singly Linked List

Time to build our custom data structure! Since our `LinkedList` class is going
to contain a series of nodes linked together, we'll start by creating `Node`
class:

```rb
class Node
  attr_accessor :data, :next_node

  def initialize(data, next_node = nil)
    @data = data
    @next_node = next_node
  end
end
```

Each node needs to keep track of some data, as well as a reference to the next
node in the list.

Next, we can build out a `LinkedList` class, with an `initialize` method where
we declare an instance variable for the `head` of the linked list:

```rb
class LinkedList
  attr_accessor :head

  def initialize
    @head = nil
  end
end
```

The `head` node is going to be the very first node in our linked list, and will
point to the next node once we start adding more elements.

### Adding Nodes

Let's say we want to recreate the data structure of dogs we had before
(`["Bulldog", "Chihuahua", "German Shepard", "Retriever", "Shiba Inu"]`). This
time we'll use a linked list instead of an array. The simplest way to do this is
to create a series of nodes and link them together using the `next_node`
attribute:

```rb
bulldog = Node.new("Bulldog")
# Bulldog
chihuahua = Node.new("Chihuahua")
bulldog.next_node = chihuahua
# Bulldog -> Chihuahua
german_shepard = Node.new("German Shepard")
chihuahua.next_node = german_shepard
# Bulldog -> Chihuahua -> German Shepard
```

While this technically qualifies as a linked list, it's not the most pleasant to
work with! We can make our data structure a bit more developer-friendly by using
the `LinkedList` class to build a list by creating an `append` method in our
`LinkedList` class.

The `append` method should add a node to the `head` of the list if the list is
empty, and add it to the end of the list if not:

```rb
class LinkedList
  attr_accessor :head

  def initialize
    @head = nil
  end

  def append(node)
    # Add element to the beginning of the list if the list is empty
    if head.nil?
      self.head = node
      return
    end

    # Otherwise, traverse the list to find the last node
    last_node = head
    while last_node.next_node
      last_node = last_node.next_node
    end

    # and add the node to the end
    last_node.next_node = node
  end
end
```

Now we can build our linked list like so:

```rb
list = LinkedList.new
list.append(Node.new("Bulldog"))
# Bulldog
list.append(Node.new("Chihuahua"))
# Bulldog -> Chihuahua
list.append(Node.new("German Shepard"))
# Bulldog -> Chihuahua -> German Shepard
```

## When to use a Singly Linked List

Linked Lists are ideal for situations when you need quick insertion and
deletion, but are more expensive than arrays when it comes to searching, since
arrays are indexed. The Big O for both insertion as well as deletion at a known
node in a linked list is `0(1)` because we don't need to update indexes for the
other elements in the list when a new element is added: we just need to adjust
which node the `next_node` points to. With an array, insertion and deletion from
anywhere other than the end are `O(n)`, because other elements need to be
reindexed.

![Pup Linked List](https://curriculum-content.s3.amazonaws.com/pup_linked_list.png)

## Conclusion

We use linked lists because they can be less expensive than arrays when it comes
to insertion and deletion within lists. Linked Lists are a very common interview
data structure, so make sure you get to know them! In the next lesson, we'll
build more methods in our `LinkedList` class.

## Resources

- [Linked list](https://en.wikipedia.org/wiki/Linked_list)
- [Practical Linked List in Ruby](https://www.rubyguides.com/2017/08/ruby-linked-list/)
