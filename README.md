# Theoretical Sorting

A Computer Science researcher claims to have come up with a sorting algorithm
that can sort arbitrary elements in $O(n)$ time based on comparisons of two
elements at a time. This would be asymptotically faster than any known general
sorting algorithm. The algorithm itself is proprietary and will be sold by a
company.

How would you verify this claim? You may assume that you have access to a
black-box implementation of the sorting algorithm, i.e. you cannot examine the
source code, but you can use it to sort any list you like. Explain in detail
your method for investigating whether X is correct, including any expected
results you would get.

Also give a theoretical argument for why X could or could not be correct, based
on the complexity of the general sorting problem we covered in class.

Add your answers to this markdown file.

# My Solution

My first response would be to call X a liar! From my general understanding,
suplemented by the sources below, and our discussions in class it is not
mathematically possible to have a comparison based sorting algorithm that
performs better than $\Theta(n \cdot \log_{2} n)$.  

To determine where an element belongs in a sorted array, a series of
comparisons must be made. In the slides from class, array positions were
used to represent these elements, but I find using variables easier to
visualize. You're given three variables: A, B, and C. Any comparison
between any two elements results in one of two posilibities: either the
former element is lesser than the latter, or the former element is greater
than or equal to the latter. This sequence of comparisons results in all
potential permutations of the input elements: ABC, ACB, BAC, BCA, CAB, and
CBA, or in more general terms a minimum of n! permutations, where n is the
number of elements being compared. In general sorting algorithms should
hopefully not produce redundant permutations, but there will be at least
n! permutations, as each of n elements must be compared to the others to
ensure proper organization.



To sort $n$ elements you
must

If you build a decision tree to determine the eprmutations of an array of values using a comparison tree, you will have a minimum of n log n leaf nodes, each of which corresponds to one of the n! potential permutations which makes up the pool of potentially sorted arrays that the input array generates.

## Sources

https://www.youtube.com/watch?v=he2jWkgIOCk  
https://www.youtube.com/watch?v=PmkzqVGjclY  
https://www.youtube.com/watch?v=H63BxAX27p0  
https://www.youtube.com/watch?v=agXcXEjg_kc  
https://www.youtube.com/watch?v=alJswNJ4P3U  
https://www.youtube.com/watch?v=WffUZk1pgXE  
