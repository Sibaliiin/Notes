*Binary search* is an efficient algorithm used to find the position of a target value within a sorted array.
It works by repeatedly dividing the search interval in half, comparing the target value to the middle element, and eliminating the half where the target cannot lie, continuing this process until the target is found or the interval is empty. If the interval is empty,  then the target was not in the array.

# Procedure
Consider an array
$\text{arr[] = \{ 2, 5, 7, 8, 12, 20, 21 ,24 ,54, 74, 75\} }$, and a target of $24$.

We first get the *middle element* from the array, in this case $20$. We *compare* the middle element to our target and *eliminate the half* where it cannot lie. Here, $20<24$, so we eliminate the left half of the array.
$$
\text{arr[] = \{ \textbf{2, 5, 7, 8, 12, 20}, 21 ,24 ,54, 74, 75\} }
$$
$$
\text{arr[] = \{21 ,24 ,54, 74, 75\} }
$$
Now, we *restart*. The middle element here is $54$.
$54>24$, so we eliminate the right half of the array.
$$
\text{arr[] = \{21 ,24 ,54, \textbf{74, 75}\} }
$$
$$
\text{arr[] = \{21 ,24 ,54\} }
$$
Again, we look at the middle element, in this case: $24$.
$24 = 24$, and *we have found* our target.

If the number of elements in our array is *even,* for example $10$, we just compute $10:2 = 5$, and we take the result as our middle element; in this case, $5$.

# Implementation
The algorithm can be written in any programming language. For this paper, I will use the C programming language.
We need to define a function, let us call it $\text{binary\_search}$. It will return the *index* where the target is located. We can use an integer for that.
## Inputs
The function will have three inputs:
- an array, which we will do the search in,
- a target, the number we are looking
- and the size of the array.

We will have an array of integers like in our example.
```c
int arr[];
```


Our target will also be an integer. 
```c
int target;
```

So the function will be:
```c
int binary_search(int arr[], int n, int target);
```
### Number of elements in the list
The size of the array will be described by the given integer:
```c
int n = sizeof(arr) / sizeof(arr[0])
```

*But*: why do we divide with the size of the first array element?

If we compute $n$ as the *size of the array*, then we would get the number of *bytes* stored in the array. Since an integer is stored in 4 bytes, the size of an array with 5 elements would be *$5 \cdot 4 = 20$*. So, we have to *divide* by the *number of bytes that describe one of our elements.* Since all of our elements are integers, we can divide by the size of the first element, which gives us the correct number of elements in the array.