Download Link: https://assignmentchef.com/product/solved-cs261-assignment-2
<br>
<h1>Part 1: Implementation of Dynamic Array, Stack, and Bag</h1>

First, complete the Worksheets 14 (Dynamic Array), 15 (Dynamic Array Amortized Execution Time Analysis), 16 (Dynamic Array Stack), and 21 (Dynamic Array Bag). These worksheets will get you started on the implementations, but you will NOT turn them in.

Next, complete the dynamic array and the dynamic array-based implementation of a stack and a bag in <strong>dynamicArray.c</strong>. The comments for each function will help you understand what each function should do.

We have provided the header file for this assignment, DO NOT change the provided header file (<strong>dynArray.h</strong>).

You can test your implementation by using the code in <strong>testDynArray.c</strong>. This file contains several test cases for the functions in <strong>dynamicArray.c</strong>. Try to get all the test cases to pass. You should also write more test cases on your own, but do not submit <strong>testDynArray.c</strong>.







<h1>Part 2: Amortized Analysis of the Dynamic Array (written)</h1>

<table>

 <tbody>

  <tr>

   <td width="41"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

Consider the <strong>push()</strong> operation for a Dynamic Array Stack. In the best case, the operation is <em>O(1).</em> This corresponds to the case where there was room in the space we have already allocated for the array. However, in the worst case, this operation slows down to <em>O(n).</em> This corresponds to the case where the allocated space was full and we must copy each element of the array into a new (larger) array. This problem is designed to discover runtime bounds on the average case when various array expansion strategies are used, but first some information on how to perform an amortized analysis is necessary.

<ol>

 <li>Each time an item is added to the array without requiring reallocation, count 1 unit of cost. This cost will cover the assignment which actually puts the item in the array.</li>

 <li>Each time an item is added and requires reallocation, count X + 1 units of cost, where X is the number of items currently in the array. This cost will cover the X assignments which are necessary to copy the contents of the full array into a new (larger) array, and the additional assignment to put the item which did not fit originally.</li>

</ol>

To make this more concrete, if the array has 8 spaces and is holding 5 items, adding the sixth will cost 1. However, if the array has 8 spaces and is holding 8 items, adding the ninth will cost 9 (8 to move the existing items + 1 to assign the ninth item once space is available).

When we can bound an average cost of an operation in this fashion, but not bound the worst case execution time, we call it amortized constant execution time, or average execution time. Amortized constant execution time is often written as <em>O(1)+</em>, the plus sign indicating it is not a guaranteed execution time bound.

In a file called <strong>amortizedAnalysis.txt</strong>, please provide answers to the following questions:

<ol>

 <li>How many cost units are spent in the entire process of performing 32 consecutive push operations on an empty array which starts out at capacity 8, assuming that the array will <em>double in capacity each time</em> a new item is added to an already full dynamic array? As</li>

</ol>

N (ie. the number of pushes) grows large, under this strategy for resizing, what is the big-oh complexity for a push?

<ol start="2">

 <li>How many cost units are spent in the entire process of performing 32 consecutive push operations on an empty array which starts out at capacity 8, assuming that the array will <em>grow by a constant 2 spaces</em> each time a new item is added to an already full dynamic array? As N (ie. the number of pushes) grows large, under this strategy for resizing, what is the big-oh complexity for a push?</li>

 <li>Suppose that a dynamic array stack doubles its capacity when it is full, and shrinks (on Pop only) its capacity byhalf when the array is half full or less. Can you devise a sequence of N <strong>push()</strong> and <strong>pop()</strong> operations which will result in poor performance (<em>O(N^2)</em> total cost)? How might you adjust the array’s shrinking policy to avoid this? (Hint: You may assume that the initial capacity of the array is N/2.)</li>

</ol>