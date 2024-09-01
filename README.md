# T2A1-B-Workbook

## Table of Contents
1. [Sorting Algorithm](#q1-identify-and-explain-the-workings-of-two-sorting-algorithms-and-discuss-and-compare-their-performanceefficiency-ie-big-o)
    - [What is a 'Sorting Algorithm?](#what-is-a-sorting-algorithm)
    - [Merge Sort](#1-merge-sort)
    - [Quick Sort](#2-quick-sort)
    - [Performance and Efficiency Comparison](#performance-and-efficiency-comparison)
2. [Searching Algorithm](#q2-identify-and-explain-the-workings-of-two-search-algorithms-and-discuss-and-compare-their-performanceefficiency-ie-big-o)
    - [What is a 'Searching Algorithm'?](#what-is-a-search-algorithm)
    - [Linear Search](#1-linear-search)
    - [Binary Search](#2-binary-search)
    - [Performance and Efficiency Comparison](#performance-and-efficiency-comparison-1)
3. [References](#references)

# Q1 Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)

## What is a 'Sorting Algorithm'?

A **'sorting algorithm'** is a method for arranging a list or array of elements in a specific order based on the user's preferences. The elements and order may take various forms such, as ascending numerical order (lowest to highest), alphabetical order, or separating even and odd numbers, among countless other options defined by the operator. [[1]](https://www.geeksforgeeks.org/sorting-algorithms/)

While there are various methods for sorting algorithms, the two algorithms to be discussed to identify and compare performances and efficiencies and provide further understanding of the algorithm are; **'Merge Sort'** and **'Quick Sort'**.

### 1. Merge Sort

**Merge Sort** is commonly seen as one of the most efficient algorithms for processing sets of values. It is a stable sorting algorithm that sorts an array using the **divide-and-conquer** technique. This technique is done by breaking down the unsorted or unordered array into smaller sub-arrays, recursively sorting them then merging the sub-arrays together to produce the final solution to the original problem, resulting in a sorted array. [[2]](https://www.w3schools.com/dsa/dsa_algo_mergesort.php)

#### Process

1. Divide: Split the array into two halves until each sub-array contains only one element, which is inherently sorted.
2. Conquer: Each individual sub-array is then sorted
3. Merge: Lastly, the sub-arrays are sorted and combined to produce a larger sorted array until it has merged into an entire sorted array.

#### Time Complexity

As each division requires a linear amount of work, the time complexity in all cases overall from best, average and worst is; ***O(nlogn)***, where there are *log n* levels of divisions (how many divisions there are) and merging at each level takes *O(n)* time.

To break it down on each case:

- Best Case: When the array is already sorted or nearly sorted. 
- Average Case: When the array is randomly ordered.
- Worst Case: When the array is sorted in reverse order. [[2]](https://www.w3schools.com/dsa/dsa_algo_mergesort.php)

Regardless of the initial arrangement of elements, merge sort will always follow the same steps; dividing the array into sub-arrays recursively, conquering by sorting elements in each sub-array then merging them into a sorted array. Since there are *log n* levels of recursion from dividing the arrays, each level requires *O(n)* time to merge into sub-arrays, resulting in an overall time complexity of ***O(nlogn)***.

#### Merge Sort Example:

To sort this array [14, 2, 9, 10, 5, 13] from lowest to highest values, we will need to break it down first to sort them in smaller groups before merging it together for the final result.

**'Divide'** in halves and break down the array into individual elements until it can no longer be divided. This process takes *log n* steps:

    [14, 2, 9, 10, 5, 13]

    Divide array in half
    [14, 2, 9] [10, 5, 13]

    Divide array again in half
    [14] [2, 9] [10] [5, 13]

    Last division of the array into individual sub-arrays each having one individual element.
    [14] [2] [9] [10] [5] [13]

**'Conquer'** the sub-array(s) by sorting element(s) in each sub-array:

    [14] [2] [9] [10] [5] [13]

    Because each sub-array only contains one element, it is considered sorted where n in log n is 6.

**'Merge'** and sort each pair of sub-arrays:

    [14] [2] [9] [10] [5] [13]

    Merge sub-array by 1 step whilst sorting
    [14] [2, 9] [10] [5, 13]

    Merge sub-arrays again whilst sorting
    [2, 9, 14] [5, 10, 13]

Merge sub-arrays for final result by comparing each single value array using either the greater than, lower than or equal to operators then adding it to the final array.
Repeat this process until the set has been sorted as one large sorted array. Each element takes *O(n)* time for each level of recursion:

    [2, 9, 14] [5, 10, 13]
    2 < 5 = [2]
    5 < 9 = [2, 5]
    9 < 10 = [2, 5, 9]
    10 < 14 = [2, 5, 9, 10]
    13 < 14 = [2, 5, 9, 10, 13]
    remaining is 14 = [2, 5, 9, 10, 13, 14]

So the result of the sorted array is **[2, 5, 9, 10, 13, 14]**. 

### 2. Quick Sort

**Quick Sort** is a sorting algorithm, similarly to the Merge Sort, uses the divide and conquer approach. Although, the quick sort algorithm selects an element called the pivot and partitions the array around this pivot. The pivot is placed in its correct position in the sorted array, with all smaller elements to the left and all larger elements to the right. The partitioning process is then applied recursively to the sub-arrays on each side of the pivot until the entire array is sorted. The key operation in a quick sort algorithm is the partitioning step, which efficiently organizes elements around the pivot. [[3]](https://www.geeksforgeeks.org/quick-sort-algorithm/)

#### Process

1. From the array, choose an element as a pivot.
2. Partition the array around the chosen pivot, ensuring all elements less than the pivot come before it and all elements greater come after the pivot.
3. Recursively sort the arrays and the sub-arrays formed from dividing the array around the pivot until only one element is left.

#### Time Complexity

The time complexity of the Quick Sort Algorithm varies depending on the choice of pivot and the elements of the input data. 

For a further breakdown by cases:

- Best Case: This occurs when the pivot divides the array into two approximately equal halves at each step. Which means each step works on half of the remaining elements, with each number of recursions and time resulting in a linear time to partition the array. Due to the linear time, this leads to an efficient sorting, catergorizing this complexity to be ***O(nlogn)***.

- Average Case: On average, Quick Sort performs well with a pivot that divides an array into relatively even partitions. This is a result in ***O(nlogn)*** complexity, where n is the number of elements in the array. With a good pivot choice, the algorithm will maintain its efficiency.

- Worst Case: This will occur when the pivot is chosen poorly, resulting in unbalanced partitions. For example, if the array is sorted, there is no movement in the pivot as the element will always be considered either the smallest or largest element in the array. [[3]](https://www.geeksforgeeks.org/quick-sort-algorithm/)

Worst Case Example:

    array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], if the pivot is [10]
    no changes are made as all elements before it is lower than [10]
    a recursive loop will continue from the sub-array = [1, 2, 3, 4, 5, 6, 7, 8, 9] with [9] being a pivot
    this will continue with pivot elements 8, 7, 6, 5, 4, 3, 2, 1 with results remaining the same each time

Due to the number of comparisons and the result of each partition step becoming smaller within the array with no changes, the time complexity in its worst case scenario is ***O(n^2)***.

#### Quick Sort Example:

Using the previous array [14, 2, 9, 10, 5, **13**] with *13* being the pivot, sort the array from lowest to highest.

**Partition** and sort the array around the pivot based on a pivot element.

    [14, 2, 9, 10, 5, 13]
    14 > 13 = nothing happens
    2 < 13 = [2, 14, 9, 10, 5, 13]
    9 < 13 = [2, 9, 14, 10, 5, 13]
    10 < 13 = [2, 9, 10, 14, 5, 13]
    5 < 13 = [2, 9, 10, 5, 14, 13]

Because our pivot 13 is at the end of the array, we need to ensure it is in the correct position.
To do so, we need to swap 13 with an element right after the last element smaller in the array than the pivot.

    in array [2, 9, 10, 5, 14, 13], 5 is the last smallest number which is smaller than 13 (pivot),
    place [13] after [5], therefore swapping [14] with [13],
    resulting in [2, 9, 10, 5, 13, 14]

**Divide** the array into sub-arrays

    from [2, 9, 10, 5, 13, 14], consider as left sub-array; [2, 9, 10, 5] as these elements are less than 13 (element < pivot)
    [13] is in its correct spot (pivot)
    [14] is in its correct spot as right sub-array, as the element is greater than 13 (element > pivot)
    dividing results = [2, 9, 10, 5] [13] [14]

**Conquer** by sorting our each sub-array [2, 9, 10, 5] [13] [14]

    For sub-array [2, 9, 10, 5], allow [5] to be the pivot and repeat steps to partition.
    2 is in its correct spot
    9 > 5 = nothing happens
    10 > 5 = nothing happens

Place pivot to 5 after the last smallest element in the sub-array

    2 < 5 = [2, 5, 10, 9]

Apply quick sort to last sub-array [2, 5, 10, 9] with 9 as pivot

    result is [9, 10]

    the conclusion to this step is: [2, 5, 9, 10] [13] [14]

**Merge** the sub-arrays to get the result of the final sorted array.

    merging the left sub-array, pivot and right sub-array
    [2, 5, 9, 10] [13] [14]

The final conclusion is **[2, 5, 9, 10, 13, 14]**.

## Performance and Efficiency Comparison

### Effiency

Merge Sort has consistency with its process through all cases, whether it is the best, average or worst cases, with a time complexity of *O(nlogn)* which makes the performance predictable to some extent. Generally, the algorithm performs fewer comparisons than quick sort and the type of elements within a data set does not affect the speed of a merge sort as it is always constant and consistent.

Quick Sort has similarities within its best and average case scenarios with a time complexity of *O(nlogn)* but falls short when faced with worst case scenario depending on the value of the pivot within the array, resulting in a time complexity in worst case scenario to be *O(n^2)*. Because the pivot could result in consistent results of being the lowest or highest element, it may result in extremely unbalanced partitions. [[5]](https://www.interviewkickstart.com/blogs/learn/quicksort-vs-merge-sort)

### Edge Cases

Merge Sort as mentioned, is consistently *O(nlogn)* in all cases, best and/or worst, regardless of the input and handles sorted arrays, unsorted arrays or arrays with duplicate elements efficiently.

However, Quick Sort in worst case occurs *O(n^2)* when pivot selection results in an highly unbalanced partition within sorted arrays or arrays with duplicate elements in comparison to a merge sort. Although this can be mitigated using randomized quick sort pivots, instead of choosing a pivot such as the first, middle or last elements, a random element will be chosen from the array and ultimately avoiding worst-case performances. [[11]](“https://www.geeksforgeeks.org/quicksort-using-random-pivoting/)

### Practical Applicability

Merge Sort is commonly used and efficiently used for linked lists where additional space for merging is not a concern whereas unlike arrays, linked lists use nodes to store elements. [[12]](https://www.freecodecamp.org/news/how-linked-lists-work/) Used in external sorting algorithms due to its predictable O(nlogn) performance, it ensures reliable performance regardless of the input data, making it a good choice for real-time systems or critical applications where worst-case scenarios must be avoided.

Quick sort preferred use is where elements are more or less evenly distributed over the range and is very efficient for sorting small data sets. It is commonly used in various standard libraries and applications and it is also generally faster than merge sort in practical scenarios for its lower constant factors and efficient in-place sorting algorithm. [[5]](https://www.interviewkickstart.com/blogs/learn/quicksort-vs-merge-sort)

# Q2 Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)

## What is a 'Search Algorithm'?

***Search Algorithms*** are an essential tool/method used to locate specific data within a collection of data structures or databases. It systematically explores data efficiently, finding the target value and determining whether the value is present within the database. Commonly used in various applications such as databases, web search engines, and more. The choice of search algorithms depends on the characteristics of the data and requirements of the search operation. The two examples we will cover and compare are ***Linear Search*** & ***Binary Search*** algorithm. [[6]](https://www.geeksforgeeks.org/searching-algorithms/)

### 1. Linear Search

A ***linear search*** algorithm is a simple and straightforward algorithm used to find a specific element within a data set, such as a list or an array. It examines each element within the data set until it finds a match, sequentially from the beginning of the data set until the end. Once the element has been located, the search will end. Although, if there is no match while searching in the data set, it will terminate the execution of the search and it must return an appropriate research. [[7]](https://www.simplilearn.com/tutorials/data-structure-tutorial/linear-search-algorithm)

### Process

1. Initialize the search, beginning from the first element of a data set. (set index to 0)
2. Compare the target element to each current element within the data set and repeat until it is found or there is no more data to compare.
3. If the search is successful, return the value to the user with its current index or position.
4. If the search is unsuccessful, return an appropriate value, such as an error or a response indicating that the element does not exist within the data set.

Linear Search Function Example: 

    def linear_search(arr, x): # where arr = array and x = target
        for i in range(len(arr)): # where i = element in array in range
            if arr[i] == x:
                return True
        return False

### Time Complexity

- Best Case: When the target value is found at the very first element of the array or list where index = 0. As there is only a need for one comparison, therefore the complexity result is ***O(1)***.
- Average Case: An average case will have the search examine about half the elements in the list before finding the target value or reaching the end of a data set. This results in a complexity of ***O(n)***.
- Worse Case: When the target value is located at the end of the data set or is not present within the data set at all. The search will need to examine and compare every element of the data set until they find the target value or reach the end of the data set. This results in the n comparisons for a list of size n = time complexity of ***O(n)***.

Worst Case Example:

    if target value is **13** in the array [14, 2, 9, 10, 5, 13].
    value of n = number of elements in the array which is 6.
    therefore O(n) = O(6).

### Linear Search Example

Search for the target value of **10** in the array [14, 2, 9, 10, 5, 13]:

Start from the beginning with index = 0 then compare the elements with the target in order.

    index 0; 10 = 14? no, move to next element
    index 1; 10 = 2? no, move to next element
    index 2; 10 = 9? no, move to next element
    index 3; 10 = 10? yes, terminate search

    result is that the target value of 10 is found at index 3.
    no further comparisons are needed with remaining elements.

### 2. Binary Search

***Binary Search*** is an efficient searching algorithm used to find a target value/element within a sorted array or list by repeatingly dividing the search interval in half, therefore eliminating half of the remaining elements in each step that significantly reduces the number of comparisons needed to find the element. The process of this algorithm results in a much faster run time compared to the linear search algorithm, especially for large datasets. [[8]](https://www.geeksforgeeks.org/binary-search/)

### Process

Before initializing a binary search, the array or list **must** be sorted in ascending or descending order.

1. Set two pointers: low (start of the array) with index = 0 and high (end of the array); thus the last element is (n - 1) where n is the total number of elements in the array.
2. Calculate the midpoint using the formula:
    - **mid = [low + high / 2]**
3. Compare the middle element with the target element.
    - If the middle element is equal to the target value, end the search and return the index position of the target value.
    - If the middle element is less than the target value, narrow the search to the left and update the **low index to mid + 1**.
    - If the middle element is greater than the target value, narrow the search to the right and update the **high index to mid - 1**.
4. Repeat process until the low index pointer exceeds the high value or when target value is found.
5. If the search is unsuccessful, terminate the search and return value indicating that the value could not be found. [[9]](https://www.w3schools.com/dsa/dsa_algo_binarysearch.php)

Binary Search Function Example:

    def binary_search(arr, x); # where arr = array and x = target
        low = 0
        high = len(arr) - 1
        mid = 0
        while low <= high:
            mid = (high + low) // 2
            if arr[mid] < x:
                low = mid + 1
            elif arr[mid] > x:
                high = mid - 1
            else:
                return True
        return False

### Time Complexity

- Best Case: When the middle element is the target on the first check. Therefore the time complexity is ***O(1)***.
- Average Case: Each step reduces the search space by half if the value comparison does not match. It results to be ***O(logn)*** where ***n*** is the number of elements in the array.
- Worst Case: With a time complexity of ***O(logn)***, it is similar to the average case, as the search space is continually halved until the target value is found or reaches the end of the data set. [[9]](https://www.w3schools.com/dsa/dsa_algo_binarysearch.php)

### Binary Search Example

Let's perform a binary search to find the number 10 in the sorted array [2, 5, 9, 10, 13, 14]:

Initialize the pointers of low and high where low index = 0 and high index = 5 as there are 6 elements within the array.

    low; i0 = 2
    high; i5 = 14

Calculate the middle index for the first iteration using the formula

    mid = [low + high / 2]
    = [0 + 5 / 2]
    = [5 / 2]
    mid = 2 = i2
    i2 = 9 which is lesser than the target value of 10
    narrow search to the right of the array updating low to mid + 1 = 3.

Calculate the middle index again using new low value

    mid = [low + high / 2]
    = [3 + 5 / 2]
    = [8 / 2]
    mid = 4 = i4
    i4 = 13 which is greater than the target value of 10
    narrow search to the left of the array updating high to mid - 1 = 3

Calculate middle index again using new low + high value

    mid = [low + high / 2]
    = [3 + 3 / 2]
    = [6 / 2]
    mid = 3 = i3
    i3 = 10 which equals to the target value.

Result = target value 10 is found in index 3.

## Performance and Efficiency Comparison 

### Effiency

While comparing both time complexity, Linear Search complexity of *O(n)* is less efficient in large data sets because it checks each element within an array sequentially in comparison to the Binary Search complexity of *O(logn)* which halves each step with each comparison but does have prerequisites, requiring the array to be sorted to perform a binary search. [[10]](https://www.shiksha.com/online-courses/articles/difference-between-linear-search-and-binary-search/#:~:text=Difference%20Between%20Linear%20and%20Binary%20Search%3A%20Linear%20vs%20Binary%20Search&text=Linear%20Search%20sequentially%20checks%20each)

### Edge Cases

Linear Search:
- When an array is empty or is not present in the array, return False as no elements are present in the array.
- In a best case scenario, the first value will match, resulting a time complexity of *O(1)* but the performance of a linear search degrades depending on the size of the array. As a worst case scenario in a larger sized array, the target value may be positioned as far as the last index of the array, therefore resulting in a time complexity of *O(n)*. [[13]](https://algocademy.com/link/?problem=linear-search&lang=py&solution=1)

Binary Search:

- When an array is empty or is not present in the array, return False as no elements are present in the array.
- Similarly to Linear Search, if the first value (middle element during comparison) matches the target value, it is considered the best scenario time complexity of *O(1)*.
- Although even in its worst scenario, binary search is more efficient than linear search through its processes during search. For every step in comparison, the number of comparisons will be halved, resulting in a faster time complexity of *O(logn)*.
- The binary search may not function at all if the array is unsorted, which is the biggest con compared to the linear search, which does not require the array to be sorted to execute a search. [[14]](https://dev.to/samfieldscc/algorithms-in-c-sorting-with-binary-search-3gj#bsa-edge)

### Practical Applicability

Linear Search is mostly suitable for small and/or unsorted data sets such as finding a book in a library or finding a file on a computer. It is useful for datasets that are small enough that the performance is acceptable. The larger the data set, the less efficient the search becoming impractical and unjustified to use due to its linear time complexity *O(n)*. Although,the pros compared to binary search is that it is much easier to implement. [[10]](https://www.shiksha.com/online-courses/articles/difference-between-linear-search-and-binary-search/#:~:text=Difference%20Between%20Linear%20and%20Binary%20Search%3A%20Linear%20vs%20Binary%20Search&text=Linear%20Search%20sequentially%20checks%20each) 

Binary search is a lot more suitable and efficient for large data sets, such as finding an item/value in a dictionary or a phone number in a phone book [[15]](https://medium.com/@imanshu822/binary-search-and-its-powerful-applications-39ae7d7bca69#:~:text=Applications%20of%20Binary%20Search&text=Its%20efficiency%20makes%20it%20ideal,phone%20numbers%20based%20on%20names.) compared to the linear search algorithm. For practical uses, it is ideal for applications where data is pre-sorted or when sorting was completed previously and requires another search to be performed (it is a prerequisite for an array to be sorted before performing a binary search) with its time complexity of *O(logn)*. If an array needs to be sorted, it can be sorted using a time complexity *O(nlogn)* before performing a binary search, resulting in faster subsequent searches.

## References

[[1]](#what-is-a-sorting-algorithm) : ---. “Sorting Algorithms - GeeksforGeeks.” GeeksforGeeks, 5 Apr. 2024, www.geeksforgeeks.org/sorting-algorithms/.
[[2]](#1-merge-sort) : “DSA Merge Sort.” Www.w3schools.com, www.w3schools.com/dsa/dsa_algo_mergesort.php.
[[3]](#2-quick-sort) : “Quick Sort Algorithm.” GeeksforGeeks, 7 Jan. 2014, www.geeksforgeeks.org/quick-sort-algorithm/.
[[4]](#2-quick-sort) : “What Is Quick Sort Algorithm: How Does It Work and Its Implementation | Simplilearn.” Simplilearn.com, www.simplilearn.com/tutorials/data-structure-tutorial/quick-sort-algorithm.
[[5]](#performance-and-efficiency-comparison) : Dipen Dadhaniya. “Difference between Merge Sort and Quicksort.” Interviewkickstart.com, Interview Kickstart LLC, 28 Aug. 2024, www.interviewkickstart.com/blogs/learn/quicksort-vs-merge-sort.
[[6]](#what-is-a-search-algorithm) : ---. “Searching Algorithms - GeeksforGeeks.” GeeksforGeeks, 2017, www.geeksforgeeks.org/searching-algorithms/.
[[7]](#1-linear-search) : A S, Ravikiran. “What Is Linear Search Algorithm? Time Complexity & Examples by Simplilearn.” Simplilearn.com, 27 July 2023, www.simplilearn.com/tutorials/data-structure-tutorial/linear-search-algorithm.
[[8]](#2-binary-search) : GeeksforGeeks. “Binary Search - GeeksforGeeks.” GeeksforGeeks, Apr. 2019, www.geeksforgeeks.org/binary-search/.
[[9]](#2-binary-search) : “DSA Binary Search.” Www.w3schools.com, www.w3schools.com/dsa/dsa_algo_binarysearch.php.
[[10]](#effiency-1) : Singh, Vikram. “Difference between Linear Search and Binary Search - Shiksha Online.” Shiksha.com, Shiksha Online, 2 Oct. 2023, www.shiksha.com/online-courses/articles/difference-between-linear-search-and-binary-search/#:~:text=Difference%20Between%20Linear%20and%20Binary%20Search%3A%20Linear%20vs%20Binary%20Search&text=Linear%20Search%20sequentially%20checks%20each.
[[11]](#edge-cases) : “QuickSort Using Random Pivoting.” GeeksforGeeks, 30 Dec. 2017, www.geeksforgeeks.org/quicksort-using-random-pivoting/.
[[12]](#practical-applicability) : Palistha. “How Does a Linked List Work? A Beginner’s Guide to Linked Lists.” FreeCodeCamp.org, 12 May 2023, www.freecodecamp.org/news/how-linked-lists-work/.
[[13]](#edge-cases-1) : “Linear Search in Python.” Algocademy.com, 2024, algocademy.com/link/?problem=linear-search&lang=py&solution=1. Accessed 1 Sept. 2024.
[[14]](#edge-cases-1) : Fields, Sam. “Algorithms Every Developer Should Know -  Binary Search.” DEV Community, DEV Community, 15 Sept. 2020, dev.to/samfieldscc/
[[15]](#practical-applicability-1) : Anshu. “Binary Search and Its Powerful Applications - Anshu - Medium.” Medium, Medium, 16 June 2023, medium.com/@imanshu822/binary-search-and-its-powerful-applications-39ae7d7bca69#:~:text=Applications%20of%20Binary%20Search&text=Its%20efficiency%20makes%20it%20ideal. Accessed 1 Sept. 2024.
