---
layout: post
title: Make the best use of them BSTs!  
---

When I think of an easy and efficient way of searching keys, the first thing that comes to my mind is a Binary Search Tree. A BST is something that' extremely simple to understand and even more simpler to implement and maintain. You build a BST as and when keys are generated/added to the store and later traverse the same tree to quickly locate (or check existence of) certain key. An age old analogy props up - the phone directory. To look up some 'Smith, John' all we need do is randomly open directory and check where we're at. If we're looking at 'Parker, Peter', we flip a few pages ahead; if its 'Snow, Jon' already we double back and take a call then. A BST works in the same way, as y'all know. So what are the pitfalls here? Why aren't BSTs the best things since Nutella? Consider this case: Lets say you have the following inputs while creating a tree : 1,5,6,45,89,134,133. So if we go by the typical BST construction approach, our tree might look like this : 

