---
layout: post
title: "mergeSort()"
description: "My javascript merge sort algorithm"
tags: [algorithms, javascript]
image:
  feature: abstract-6.jpg
  credit: dargadgetz
  creditlink: http://www.dargadgetz.com/ios-7-abstract-wallpaper-pack-for-iphone-5-and-ipod-touch-retina/
comments: true
share: true
---

Today I will be showing y'all my implementation of a [merge sort](http://en.wikipedia.org/wiki/Merge_sort) in javascript. Implementing merge sorts is a very popular interview exercize. Our solution does the following --

  1. If the unsorted array's length is less than two, it's already sorted. In this case we just return the unsorted array.
  2. We split the unsorted array in half.
  3. Use recursion to keep splitting the sub arrays.
  4. Merge the sub array back to form your sorted result array.

{% highlight javascript linenos %}
{% raw %}

// the following merge function is going to be the workhorse of our implementation.
// it takes 2 arrays and merges them into one ordered array.
var merge = function(leftHalf, rightHalf){
  var result = [];

  // We need to check whether the first or second array starts with the smaller number
  // and push it into our result array.
  while (leftHalf.length && rightHalf.length) {
    if (leftHalf[0] <= rightHalf[0]) {
      result.push(leftHalf.shift());
    } else {
      result.push(rightHalf.shift());
    }
  }

  while (leftHalf.length){
    result.push(leftHalf.shift());
  }
  while (rightHalf.length){
    result.push(rightHalf.shift());
  }
  return result;
}

// I've added the optional parameter fn and a few lines of code to allow for polymorphism*.
// Polymorphism allows our mergeSort to work with other datatypes, such as objects.
var mergeSort = function(array, fn){
  fn = (typeof(fn) === 'function') ? fn : function(a, b){
    if (a < b){
      return - 1;
    } else if (a === b){
      return 0;
    } else {
      return 1;
    }
  };

  // the base case for our recursion.
  if (array.length < 2){
    return array;
  }

  // split our input array in half
  var half = parseInt(array.length / 2);
  var leftHalf   = array.slice(0, half);
  var rightHalf  = array.slice(half, array.length);

  // using recursion to continue splitting our array, and then feeding the results
  // to our merge function to construct our final output array.
  return merge(mergeSort(leftHalf), mergeSort(rightHalf));
}

{% endraw %}
{% endhighlight %}

You can read more about [polymorphism](http://en.wikipedia.org/wiki/Polymorphism_(computer_science)) here.

If would love for y'all to hit me up with any questions or comments on this blog post.
Hope it helped!
