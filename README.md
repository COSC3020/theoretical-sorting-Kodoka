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

# How I Would Text X's Claim, and Expected Results

I think the best way to test X's claim would be to feed the black-box
implementation of their sorting algorithm fully random arrays, sorted -
ascending arrays, and sorted - descending arrays in various sizes, for
example of 1,000, 2,000, 4,000, etc. elements.

Running their sorting algorithm with sorted, unsorted, and reverse-sorted
arrays should let me see how their algorithm performs under the best and
worst circumstances, and using inputs of various sizes will allow me to
grather enough data to graph their algorithms performances, which,
assuming their claim is true, should show the running time scaling
linearly with n, despite the favorability of the input.

What I suspect I'll see instead is something like Bubble or Insertion
sort, where in the best case the algorithm performs in $O(n)$, and in
worst case O(n^2)$. Whether X maliciously lied about the performance
of their algorithm to try and get rich, there was a flaw in the timing
code, there was a flaw in the code generating test cases, or a flaw in
the code actually sorting, I doubt their algorithm actually performs
that well in all scenarios.

# My Reaction to X's claim, and Why it Could or Could Not Be Correct

My first response would be to call X a liar! From my general understanding,
suplemented by the sources below, and our discussions in class it is not
mathematically possible to have a comparison based sorting algorithm that
performs better than $\Theta(n \cdot \log_{2} n)$.  

To determine where an element belongs in a sorted array, a series of
comparisons must be made. In the slides from class, array positions were
used to represent these elements, but I find using variables easier to
visualize. So I'll be working with $A$, $B$, and $C$.  

When comparing any two elements, we can have one of two results: the
former element is smaller than the latter, or the former element is
larger than the latter. Using the results of these comparisons, we can
produce a decision tree, which is ostensibly a binary tree with true
or false paths resulting from each comparison.  

Allowing $A$, $B$, and $C$ to represent indeterminant values, we can
compare sequentially compares all elements to produce a tree where the
terminating nodes represent all potential permutations the sorted input
could produce. For $A$, $B$, and $C$ the potential permutations would be:
$ABC$, $ACB$, $BAC$, $BCA$, $CAB$, and $CBA$. Or $n!$ permutations.

Sometimes we'll get shorter paths. For example: $A < B < C$. In this
scenario comparing $A$ to $B$ results in a true path, Then comparing
$B$ to $C$ results in another true path. As $A < B$, and $B < C$, the
comparison of $A$ to $C$ is superfluous, meaning we only needed two
comparisons to establish the proper sorting, but in the worst case, for
example: $A < B$, $B > C$. Comparing $A$ to $B$ results in a true path,
then comparing $B$ to $C$ results in a false path. We established $A < B$
and $B > C$, but this doesn't reveal anything about the relationship
between $A$ and $C$, we must directly compare the two to determine which
permutation has all three elements in properly sorted order. For our
input of 3 elements, in the worst case, we must perform $\log_{2} n$
comparisons, which is also the minimum height of our decision tree,
as to perform those $\log_{2} n$ comparisons, we need a tree with
adequate height to perform $\log_{2}$ comparisons.

Now, as there are $n!$ potential permuttations for $n$ elements, we know
our decision tree must have at least $n!$ terminating nodes. We also know
that a binary tree of height h can result in, at most, $2^h$ leafs, so we
know $2^h \geq n!$. Taking $\log_{2}$ of both sides gives us $h \geq
\log_{2} n!$, which gives us $n \cdot \log_{2} n$ according to Stirling's
approximation.

All of that is to say I'm accusing X of being a liar on the grounds that
mathematically, their claim isn't possible; however, playing the Devil's
advocate for just a moment, I will concede I don't know a whole lot about
quantum computing, but based on my very rudimentary understanding, perhaps,
if that is the basis technology for his sorting algorithm, perhaps this is
possible, as all the true and false branches are established when the
quantum state colapses, or something like that.

## Sources

I read through and referenced material from the slides in class.

I also went down a rabbit hole with watching videos regarding this subject.
Many of the following videos covered the same material that the others
did, and what was covered in class, but I did watch all of them to round
our my understanding of theoretical sorting limits of comparison algorithms:

https://www.youtube.com/watch?v=he2jWkgIOCk  
https://www.youtube.com/watch?v=PmkzqVGjclY  
https://www.youtube.com/watch?v=H63BxAX27p0  
https://www.youtube.com/watch?v=agXcXEjg_kc  
https://www.youtube.com/watch?v=alJswNJ4P3U  
https://www.youtube.com/watch?v=WffUZk1pgXE  
