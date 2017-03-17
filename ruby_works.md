#Arrays - Sorting, Filtering (Select), Transforming, Multi-Dimensional Arrays

> 1) Find even and odd number from given array? 
>> arr = [1,2,3,4,5,6,7,8]

Ans: 
```ruby
arr.select{|x| x%2==0}

arr.select{|x| x%2==1}
```

> 2) Write own sorting function and make given array sort in acending order.

Ans:
```ruby
arr = [0,1,2,3,4,5,6,7,8,9,10]

def f(x)
	x*x-x*x*x+x+20
end

sortArray = arr.sort_by{|a| f(a)}
```
=> [10, 9, 8, 7, 6, 5, 4, 3, 2, 0, 1] 

>>Check really working?
```ruby
sortArray.map{|a| f(a)}
```
=> [-870, -619, -420, -267, -154, -75, -24, 5, 18, 20, 21]

> 3) Applying a function to each element of a list. This can be done using the map method. Suppose, we want a new array, such that, for every element, x in the original array, the new array contains 2x+10.

Ans:
```ruby
arr = [0,1,2,3,4,5,6,7,8,9,10]

arr.map{|a| 2*a+10}
```
> 4) How you could initialize  multi-dimensional array in Ruby?

Ans:
```ruby
Array.new(10){Array.new(5){0}}
```
Or you could use 'matrix' which is a package bundled with Ruby.
```ruby
require 'matrix'
m = Matrix[ [0,1,2],[2,3,4]]

m.element(0,1) #Accessing a particular element
m.column(1)    #Accessing a particular column
m.row(1)       #Accessing a particular row
```

# Computing Factorials Recursively : An Example of Recursion

```ruby
# Factorial formula
# n! = n * (n-1) * (n-2) * .... 1
# Let's use recursion to solve this in Ruby.

def recursiveFactorial(x)
	return 1 if x == 1
	return x* recursiveFactorial(x-1)
end

puts "Enter a Number"
N = gets().to_i
puts "The Factorial is:"
puts recursiveFactorial(N).to_s

```
#The Queue

Queue is a specialized data storage structure (Abstract data type). Unlike, arrays access of elements in a Queue is restricted. It has two main operations enqueue and dequeue. Insertion in a queue is done using enqueue function and removal from a queue is done using dequeue function.

##Algorithm:
Queue structure is defined with fields capacity, size, *elements (pointer to the array of elements), front and rear.

##Functions –
 1. createQueue function– This function takes the maximum number of elements (maxElements) the Queue can hold as an argument, creates a Queue according to it and returns a pointer to the Queue. 
 2. enqueue function - This function takes the pointer to the top of the queue Q and the item
 (element) to be inserted as arguments. Check for the emptiness of queue
 3. dequeue function - This function takes the pointer to the top of the stack S as an argument and will then dequeue an element.
 4. front function – This function takes the pointer to the top of the queue Q as an argument and returns the front element of the queue Q. 

##Properties –

 1. Each function runs in O(1) time.
 2. It has two basic implementations
> Array-based implementation – It’s simple and efficient but the maximum size of the queue is fixed.

> Singly Linked List-based implementation – It’s complicated but there is no limit on the queue size, it is subjected to the available memory.

##Example:
>First in First Out data structure (FIFO). Like people waiting to buy tickets in a queue - the first one to stand in the queue, gets the ticket first and gets to leave the queue first. Documentation of the various operations and the stages a queue passes through as elements are inserted or deleted. C Program source code to help you get an idea of how a queue is implemented in code.

#Stack

Stack is a specialized data storage structure (Abstract data type). Unlike, arrays access of elements in a stack is restricted. It has two main functions push and pop. Insertion in a stack is done using push function and removal from a stack is done using pop function. It is therefore, also called Last-In-First-Out (LIFO) list. Stack has three properties: capacity stands for the maximum number of elements stack can hold, size stands for the current size of the stack and elements is the array of elements.

##Algorithm:

Stack structure is defined with fields capacity, size and *elements (pointer to the array of elements).

##Functions – 
1. createStack function– This function takes the maximum number of elements (maxElements) the stack can hold as an argument, creates a stack according to it and returns a pointer to the stack. It initializes Stack S using malloc function and its properties.
2. push function - This function takes the pointer to the top of the stack S and the item (element) to be inserted as arguments. Check for the emptiness of stack
3. pop function - This function takes the pointer to the top of the stack S as an argument.
4. top function – This function takes the pointer to the top of the stack S as an argument and returns the topmost element of the stack S. 

##Properties of stacks:
1. Each function runs in O(1) time.
2. It has two basic implementations
> Array-based implementation – It is simple and efficient but the maximum size of the stack is fixed.

> Singly Linked List-based implementation – It’s complicated but there is no limit on the stack size, it is subjected to the available memory.

##Example:
Last In First Out data structures ( LIFO ). Like a stack of cards from which you pick up the one on the top ( which is the last one to be placed on top of the stack ). Documentation of the various operations and the stages a stack passes through when elements are inserted or deleted. C program to help you get an idea of how a stack is implemented in code.

#Efficient Sorting Algorithms:

##Insertion Sort
Insertion sort uses linear search to find the location of the 1st element in the unsorted list, in the sorted portion of the list. It is an elementary sorting algorithm best used to sort small data sets.

###Algorithm:
Insertion sort starts with a sorted list of size 1 and inserts elements one at a time. It continues inserting each successive element into the sorted list so far.

1. Suppose if the array is sorted till index i then we can sort the array till i+1 by inserting the (i+1)th element in the correct position from 0 to i+1.
2. The position at which (i+1)th element has to be inserted has to be found by iterating from 0 to i.
3. As any array is sorted till 0th position (Single element is always sorted) and we know how to expand, we can sort the whole array.

###Properties:

1. Best case performance – When the array is already sorted O(n). Total number of comparisons: N – 1 and total number of exchanges: N – 1.
2. Worst case performance – When the array is sorted in reverse order O(n2). N-1 iterations of comparison and exchanges.
3. Average case performance – O(n2)
4. It is sensitive to the input as the number of comparison and exchanges depends on the input.
5. It does not require any extra space for sorting, hence O(1) extra space.

###Example:
```ruby
# Insertion Sort ************************
# Insertion Sort -> A popular quadratic sorting algorithm with O(n^2) complexity
def insertionSort(arr)
    for size in 2..arr.length
        # Remember, this is a zero-start array
        element = arr[size-1]   

        # Bring this element down to its appropriate position
        # elements[0] ... elemets[size-2] are already in a sorted order
        index = size - 2
        while(index >= 0) && (element < arr[index])
            arr[index + 1] = arr[index]
            index-=1
        end
        arr[index+1] = element
    end
        
end

puts "Original Array :"
original_array=[2,19,5,4,3,14,2]
p original_array
puts "Sorted Array Using Insertion Sort:"
insertionSort(original_array)
p original_array

=begin
Sample Output :
puts "Original Array :"
original_array=[2,19,5,4,3,14,2]
p original_array
puts "Sorted Array Using Insertion Sort:"
insertionSort(original_array)
p original_array
=end
```