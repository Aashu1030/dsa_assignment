# Sorting Algorithm Performance Comparison

This program implements four different sorting algorithms (Bubble Sort, Selection Sort, Insertion Sort, and Merge Sort) and measures their performance by counting the number of comparisons and swaps performed on randomly generated data.

## Data Structures

The program uses simple arrays and global counters to manage data and track performance:

- **arr[n]**: A dynamically sized integer array that stores the elements to be sorted. The size is determined by user input at runtime.

- **n**: An integer variable representing the number of elements in the array.

- **comparisons**: A global long integer that counts the total number of element comparisons made during the sorting process. This counter is incremented each time two elements are compared.

- **swaps**: A global long integer that tracks the total number of swap or move operations performed. For Bubble, Selection, and Insertion Sort, this represents actual swaps. For Merge Sort, it counts the number of moves during the merge operation.

- **choice**: An integer variable storing the user's selection of which sorting algorithm to execute.

The use of global counters allows all sorting functions to update the same comparison and swap counts, enabling accurate performance measurement across different algorithms.

## Functions Implemented

### 1. `void swap(int *a, int *b)`
**Purpose**: Exchanges the values of two integers and increments the swap counter.

This utility function takes two pointers to integers and swaps their values using a temporary variable. It also increments the global swaps counter to track the number of swap operations performed. This function is used by Bubble Sort and Selection Sort to exchange elements, and serves as a fundamental building block for comparison-based sorting.

### 2. `void bubbleSort(int arr[], int n)`
**Purpose**: Sorts the array using the Bubble Sort algorithm.

This function implements Bubble Sort by repeatedly stepping through the array, comparing adjacent elements, and swapping them if they are in the wrong order. The outer loop runs n-1 times, and the inner loop compares adjacent pairs, with the range decreasing each iteration as larger elements "bubble up" to their correct positions at the end. Each comparison increments the comparisons counter, and swaps are counted within the swap function. Bubble Sort has a time complexity of O(n²) in average and worst cases.

### 3. `void selectionSort(int arr[], int n)`
**Purpose**: Sorts the array using the Selection Sort algorithm.

This function implements Selection Sort by dividing the array into sorted and unsorted portions. In each iteration, it finds the minimum element from the unsorted portion and swaps it with the first unsorted element. The outer loop runs n-1 times, and for each iteration, the inner loop finds the index of the minimum element. Comparisons are counted during the search for the minimum, and only one swap per outer iteration is performed (if needed). Selection Sort has O(n²) time complexity but performs fewer swaps than Bubble Sort.

### 4. `void insertionSort(int arr[], int n)`
**Purpose**: Sorts the array using the Insertion Sort algorithm.

This function implements Insertion Sort by building the sorted array one element at a time. It picks each element (starting from the second) and inserts it into its correct position in the already sorted portion. The function uses a key variable to hold the current element and shifts larger elements to the right. Each comparison and shift operation is counted. Insertion Sort is efficient for small or nearly sorted arrays and has O(n²) worst-case complexity but O(n) best-case when the array is already sorted.

### 5. `void merge(int arr[], int l, int m, int r)`
**Purpose**: Merges two sorted subarrays into a single sorted array.

This helper function is used by Merge Sort to combine two sorted subarrays. It creates two temporary arrays to hold the left and right portions, then merges them back into the original array in sorted order. The function compares elements from both subarrays and places the smaller element into the result array. Each comparison is counted, and when an element from the right subarray is selected, it's counted as a swap since it represents a move operation. The merge operation runs in O(n) time where n is the total number of elements being merged.

### 6. `void mergeSort(int arr[], int l, int r)`
**Purpose**: Sorts the array using the Merge Sort algorithm recursively.

This function implements the divide-and-conquer Merge Sort algorithm. It recursively divides the array into two halves until single elements remain (which are inherently sorted), then merges them back together in sorted order using the merge function. The middle point is calculated, and the function calls itself on the left and right halves before merging. Merge Sort has O(n log n) time complexity in all cases, making it more efficient than the quadratic sorting algorithms for large datasets, though it requires additional space for the temporary arrays.

### 7. `void printArray(int arr[], int n)`
**Purpose**: Displays all elements of the array in a single line.

This utility function iterates through the array and prints each element separated by a space, followed by a newline. It provides a clear visualization of the array contents before and after sorting, allowing users to verify the sorting operation was successful.

## Organization of main() Method

The main function orchestrates the entire program through the following sequence:

1. **Variable Declaration**: Variables for array size (n) and user choice (choice) are declared, along with the array itself.

2. **Input Array Size**: The program prompts the user to enter the number of elements they want to sort.

3. **Array Declaration**: An integer array of size n is declared to hold the elements.

4. **Random Number Generation**: The random number generator is seeded with the current time using `srand(time(NULL))` to ensure different random numbers on each run. A loop generates n random integers between 1 and 1000 using `rand() % 1000 + 1`.

5. **Display Unsorted Array**: The original unsorted array is printed so the user can see the initial data.

6. **Menu Display**: A menu showing the four available sorting algorithms is displayed with numbered options.

7. **Algorithm Selection**: The user enters their choice (1-4) to select which sorting algorithm to use.

8. **Counter Reset**: The global comparisons and swaps counters are reset to 0 to ensure accurate measurement.

9. **Sort Execution**: A switch statement executes the chosen sorting algorithm. For Merge Sort, the initial call uses indices 0 and n-1 to sort the entire array.

10. **Display Sorted Array**: The sorted array is printed to show the final result.

11. **Performance Metrics**: The total number of comparisons and swaps/moves performed during sorting is displayed, allowing performance analysis.

12. **Program Termination**: Returns 0 to indicate successful execution.

## Sample Output

### Run 1: Bubble Sort on 10 Elements
