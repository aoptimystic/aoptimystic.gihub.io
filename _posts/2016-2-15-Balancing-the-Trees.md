---
layout: post
title: Make the best use of them BSTs!  
---

When I think of an easy and efficient way of searching keys, the first thing that comes to my mind is a Binary Search Tree. A BST is something that's extremely simple to understand and even more simpler to implement and maintain. You build a BST as and when keys are generated/added to the store and later traverse the same tree to quickly locate (or check existence of) certain key. An age old analogy props up - the phone directory. To look up some 'Smith, John' all we need do is randomly open directory and check where we're at. If we're looking at 'Parker, Peter', we flip a few pages ahead; if its 'Snow, Jon' already we double back and take a call then. A BST works in the same way, as y'all know. So what are the pitfalls here? Why aren't BSTs the best things since Nutella?

Consider this case: Lets say you have the following inputs while creating a tree :

1,  5,  6,  45,  89,  134, 133. 

So if we go by the typical BST construction approach, our tree might look like this : 

  <img src={{ site.url }}/images/BinaryTree1.png align="middle">

If we later want to search for 133, we have to traverse the whole tree until we hit 134, and then take left. Number of comparisons? 6. 
Now, if our tree was only like this :

  <img src={{ site.url }}/images/BinaryTree2.png align="middle">
              
Number of comparisons? 3! Although, 3 and 6 are not that different, but imagine if we are talking about several million records. This overhead save will certainly prove significant. So the point is, even if you are using a BST, its all about how you're shaping it. More often than not, unless you have the keys already, a BST is created like our first approach as its the easiest and fastest. There is a way to create optimal BSTs (self balancing trees, AVL trees, etc.) but they make insertion fairly slower. What I am going to talk about today is balancing a tree after its creation. What more, in O(N) time, which makes it even more awesome! 

The method is very similar to DSW Algorithm (Day, Stout and Warren). I have borrowed their first step and kind of tweaked the second one to make it a little more simpler. Although the result won't be a text-book DSW balanced tree, it would be highly close enough with equal number of max comparisons. 

        Step 1. Generate a Linked List.

We have a tree. Good. A BST.Great! What can make our life even better? Why, a linked list of course! So there are two ways to go about it. One, we can print out the inorder traversal of BST and add the elements to a List. Else, we can do it programatically by rotating every lchild we come across to make the BST highly skewed until no node has any lchild present but only the rchildren remain. Something like this : 

<img src={{ site.url }}/images/BinaryTree3.gif align="middle">

[Image credit: <a href ="http://penguin.ewu.edu/~trolfe/DSWpaper/"> here</a>] 
So the code looks like :-

{% highlight java %}
public void balanceIt(){
//Create a Pseudo root first
  Node PSEUDO = new Node(0);
  PSEUDO.rchild = this.root;

  Node iterator1 = PSEUDO.rchild;
  Node iterator2 = PSEUDO;
  while(iterator1 != null){

   if(iterator1.lchild != null){
    Node temp = iterator1.lchild;
    iterator2.rchild = temp;
    iterator1.lchild = temp.rchild;
    temp.rchild = iterator1;
    iterator1 = temp;
   }
  else{
   iterator2 = iterator2.rchild;
   iterator1 = iterator1.rchild;
  }

}
{% endhighlight %}
            
