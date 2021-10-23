# Singly Linked List Data Structure

## Learning Goals

- Identify the use cases for a `Linked List`
- Demonstrate common methods for a `Linked List`
- Differentiate between a `Singly Linked List` and an `array`

## Introduction

In this lesson, we'll learn what a `Singly Linked List` is, along with how to build and implement one in a class along with some of
its common methods to get an understanding of what the differences between a `Singly Linked List` and an`Array` are.

## Why Linked Lists?

We use linked lists because they take less insertion time when we have a lot of data. >> elaborate << Think about if we have a sorted alphabet array of 10 elements representing letters.

```rb
[  "A", "B", "C", "D", "E", "F", "H", "I", "J", "K" ]
   [0]  [1]  [2]  [3]  [4]  [5]  [6]  [7]  [8]  [9]
```

After creating our array, we realize we forgot to add one letter in our array! If we added the letter "G" to the end of the array, it would no longer be sorted, so we would need  to  _insert_ the "G" element into the array in the correct index, which would be  6. Because there  is already  an element in the 6th index, and more elements in the sequential indexes, all of those elements would have  to be  shifted down a  spot,  and given a new index. Because this is a smaller array it doesn't seem like the biggest deal to move the last 4 elements down a place, but as you can imagine, if we had an array of 100s or thousands or even millions of elements, reindexing *all* of those elements would take a really long time! This is where linked lists come in handy! 

# pupper array image here

## Defining a Singly Linked List

In a `Linked List`, instead of every element (called a `Node`) having an index like in an array, each `node` is just pointing to the next `node`. These `nodes` can be sorted or unsorted and can be any data type. `Nodes` aren't indexed in a singly linked list as they are in an array; instead, they only know about the element in front of them. Think of it like a train, each car is connected to the next car, which is connected to the next car, and so forth. In an array we can say “Give me the sixth element,” but in a linked list we have to start at the beginning of the train, and go from the first car, to the second car, and so forth. Let's take a look at how we can build this out. 

# pupper linked list image here

The nodes in a linked list each have a value, and a pointer to another node, otherwise pointing to nil if it is at the end of the list.

We'll start by building out a `LinkedList` class, with an `initialize` method containing variables for the `head` and `tail` of the Linked List. 

```rb
Class LinkedList

   def initialize
      @head = self.head
      @tail = self.tail
   end 

end
```

The `head` node is going to be the very first node in our singly linked list, and will point to the next node. The `tail` of our singly linked list will be the last node in the list.

The next step is to set up a `Node` class. 

```rb
Class Node
   attr_accessor :data, :next_node

   def initialize(data, next_node = nil)
      @data = data
      @next_node = next_node
   end
end
```

By adding an attribute accessor to our Node class, we are telling our program that we can't create a new instance of a `Node` without the data as well as a pointer to the next node. We set the default value of `next_node` to nil so that by default if a new Node is being added to the end of our linked list (the tail) then it doesn't need to point to anything other than `nil`.


## Singly Linked List Methods

Let's say we want to recreate the data structure of letters we had before (`[  "A", "B", "C", "D", "E", "F", "H", "I", "J", "K" ]`) but this time we'll use a Singly Linked List instead of an array.
We want to start by adding the first letter so we need to create an `append` method in our `LinkedList` class.

```rb
Class LinkedList

   def initialize
      @head = self.head
      @tail = self.tail
   end 

   def append(letter)
      
      # Create a new node, if there are no nodes in our singly linked
      # list already, we will assign this new node to be the head.
      this_node = Node.new(letter)

      if @head.nil?
         @head = this_node
      end

      current = @head  
      # We can will assign the value of head to current, and unless
      # the value of current.next_node is nil, we will assign it to current.next_node
      until current.next_node.nil?
         current = current.next_node
      end

      # Finally, we will point the current(last node) to our newly created node, this_node
      current.next_node = this_node
   end
end
```


## When to use a Singly Linked List
   Linked Lists are ideal for situations when you need quick insertion and deletion, but are more expensive than arrays when it comes to searching. The Big O for both interstion as well as deletion in a linked list is 0(1) because we don't need to update indexes or anything when we add or remove a node; we just need to readjust pointers. Where as with an array, intertion and deletion are O(n), because of reindexing.

## Conclusion
   We use linked lists because they are way less expensive than arrays when it comes to insertion and deletion within lists. Linked Lists are a very common interview data structure so make sure you get to know them!
