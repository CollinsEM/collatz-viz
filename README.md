# collatz-viz

This is a single page HTML/CSS/JS application that displays a
hierarchical listing of the binary representation of just the odd
values in the Collatz sequence. I find this particular visualization
rather interesting because of fairly obvious patters that can be seen
in the binary representations of the numbers in each branch of the
hierarchy.

# Usage

Hover over nodes to see their decimal (base-10) values.

Click on a node to open/close it.

Shift-click (hold down the SHIFT key and click) on a node to add more
child nodes.

Shift-click on the root node (***) to generate more Tier 1 nodes.

# NOTES

If a node does not open, then it is evenly divisble by 3. Since no
other odd values will collapse to a node that is evenly divisible by
3, such nodes can only be reached by multiples of 2 of that value.

The node for 1 is disabled since it will just recursively generate the
values in the first column.

# Observations

Within a single nested list of values, each subsequent value is
bit-shifted left twice and a 1 added to the end. This is consistent
with the formula that generates these values: (4*M+1), where M is the
previous value in the sequence. Each of the values in this sequence
are odd, and they will all collapse to the same number after one
application of the 3n+1 rule followed by as many applications of the
n/2 rule as necessary to arrive at an odd number.

               T1
00000000001     1
00000000101     5
00000010101    21
00001010101    85
00101010101   341
10101010101  1365
...

If you just look at the first nested values under each of the Tier 1
(trunk) values, you will see another interesting pattern. Aside from
the nodes that don't expand (due to them being evenly divisible by 3),
you can clearly see that the first values in the nested lists follow a
recognizable pattern.

                   T2       T1
00000000000001      1 ->     1
00000000000011      3 ->     5
00000001110001    113 ->    85
00000011100011    227 ->   341
01110001110001   7281 ->  5461
11100011100011  14563 -> 21845
...

Subsequent values under each of these initial values follow the
bit-shifting pattern mentioned above (4M+1).
