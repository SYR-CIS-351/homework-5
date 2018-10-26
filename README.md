# Homework 5, Third(?) Try

### Details

* **Due:** October 31 (end of the day) on gitHub.
  <br>
  Be sure to include your coversheet.


* **Reading:**
  Through Chapter 3 of [TMLL](http://cglab.ca/%7Eabeinges/blah/too-many-lists/book/)

* **Starter Code**
  See the course website.
  
-------------------------------------------------------------------------------

##### Problem: A plusher version of persistent binary search trees

<!--

* [Here is the link to that homework description.](https://github.com/cis198-2016s/homework/tree/master/hw02)
  You can grab their starter code, but you won't be happy. 

* **[New: October 22]**  We are switching to using TMLL's 
  [Chapter 3: A Persistent Singly-Linked Stack](http://cglab.ca/%7Eabeinges/blah/too-many-lists/book/third.html)
  as a basis for our search tree.  So the trees will be immutable, but we'll make a lot of trees to make up 
  for that.  
-->

* Build upon what I have on the course webpage, or go your own direction.  

* Here are the changes I want to see:

1. Make the BST generic.  The type parameter `T` needs to satisfy the `Ord` and `Clone` traits.  
   So, for example, your `impl` block for `Link` will change from:
   ~~~
   impl Link { /* stuff * }
   ~~~
   to 
   ~~~
   NEW  impl<T: Ord + Clone> Link<T> { /* stuff */ }
   ~~~  
   Also you might have to add a couple `.clone()`s where the compiler fusses about moving things of type `T`. 

2. Add methods
~~~
pub fn min_val(&self) -> Option<&T) 
pub fn max_val(&self) -> Option<&T> 
pub fn depth(&self) -> u32 
pub fn range(&self, low: &T, hi: &T) -> Vec<&T>
~~~    
Where

* `t.min_val()` returns `None` if `t` is empty and otherwise returns `Some(x)` where `x` is the minimum value in `t`.
* `t.max_val()` returns `None` if `t` is empty and otherwise returns `Some(x)` where `x` is the maximum value in `t`.
* `t.depth()` returns the *depth* of `t`, i.e., the number of nodes on a longest path from the root of `t` to a leaf.
  (So an empty tree has depth 0.)
* `t.range(low,high)` returns a `Vector` of the elements of `t` between `low` and `high` in order. For example, 
  the follow test should succeed. 
  ~~~
  let mut t = BST::new();
  t = t.insert(2);
  t = t.insert(6);
  t = t.insert(27);
  t = t.insert(4);
  t = t.insert(0);
  assert_eq!(t.range(&2,&10),[&2,&4,&6]);
  ~~~
  
* I want simple (but not too simple) tests of your methods.  

* For more on persistent binary trees, see <https://en.wikipedia.org/wiki/Persistent_data_structure#Trees>
  in <https://en.wikipedia.org/wiki/Persistent_data_structure>.
  
* Here are things I found helpful:
  + Trying the compiler's advice is a good idea, even if it doesn't always work.
  + `Ord::min` and `Ord::max`
  + The `push` and `append` methods of `Vec`
 
<!--
* Here are things I want implemented.
  + the basic data type definitions
  + a `new` function
  + a `search` function
  + a `insert` function
  + tests of all of the above

* *Still* expect trouble.
* We'll have a another debugging session in Wednesday's class. 

* [Here is an implementation of a binary search tree along somewhat different lines](https://gist.github.com/aidanhs/5ac9088ca0f6bdd4a370).
  You may still borrow ideas from here.
  + [bst.rs](http://www.cis.syr.edu/~royer/cis400/code/bst.rs)
  + [dot.rs](http://www.cis.syr.edu/~royer/cis400/code/dot.rs)
-->
