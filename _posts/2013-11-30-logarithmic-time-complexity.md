---
layout: post
title: "Logarithmic Time Complexity"
description: "Introduction to logarithmic time complexity"
tags: [algorithms, javascript, time complexity]
image:
  feature: abstract-6.jpg
  credit: dargadgetz
  creditlink: http://www.dargadgetz.com/ios-7-abstract-wallpaper-pack-for-iphone-5-and-ipod-touch-retina/
comments: true
share: true
---

[Time complexity](http://dictionary.reference.com/browse/time+complexity) refers to the relationship between how long an algorithm takes to complete calculations on a number of items. It's important as software engineers to consider the time complexity of your algorithms, so we can make better informed decisions in writing algorithms to solve problems. Something to note is that when talking about the time complexities of algorithms, we generally talk about the worst case scenerios. Time complexity can be determined by counting the number of operations that need to be performed by an algorithm, and is often expressed in [big O notation](http://stackoverflow.com/questions/487258/plain-english-explanation-of-big-o/487278#487278).

Today we will be discussing logarithmic time complexity. An algorithm is considered to have logarithmic complexity when the number of operations per unit of work needed to be done decreases as the units of work increase. This means that functions with a logarithmic complexity are very efficient.

The following is an example of an algorithm that takes logarithmic time that I found on [Wikipedia](http://en.wikipedia.org/wiki/Time_complexity#Logarithmic_time).
{% highlight javascript linenos %}
{% raw %}
// We assume that console.log and str.substring run in constant time
// Function to recursively print the right half of a string
var right = function(str){
  var length = str.length;

    // Helper function
    var help = function(index){

      // Recursive Case: Print right half
      if(index < length){

        // Prints characters from index until the end of the array
        console.log(str.substring(index, length));

        // Recursive Call: call help on right half
        help(Math.ceil((length + index)/2));
      }

    // Base Case: Do Nothing
  }
  help(0);
}

{% endraw %}
{% endhighlight %}

Last week's post about [mergeSort()](http://mayho.github.io/merge_sort/) is also an example of a function that has a logarithmic time complexity, specifically the portion of the algorithm that separated the input string into individual characters by recursively splitting the string in half.