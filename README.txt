1) 
The disaggregate function first saves the $s registers and prints out the array input while saving the sum of the array.
Then, if depth is 0 or the array length is 1, exit the function and return back to the caller function.
If not, calculate the average of the array elements. If an element in the array is less than the average, save it to small_array. Otherwise, save it to large_array.
Then, call disaggregate twice - one for the small_array as input, and one for the large_array as input.
Finally, once both functions have finished, we can load the $s registers back in from the stack and return.


2)
Assuming that the array length is at most 10, decreasing the array length does not change the space used on the stack.
This is because the first array is stored as static data (not part of the stack), and each recursive call stores the resulting array in the buffer array.
This buffer array was already set to 100 words (400 bytes), meaning that we did not use less space by using a smaller array.

Similarly, changing the array values does not affect the stack space used (as long as we use a value that fits in a word - 4 bytes), since the buffer array has already been allocated.

With depth, however, decreasing the depth lowers the amount of recursive calls performed (and vice-versa for increasing depth). Because of this, we will store the values of $s and $ra registers on the stack less times.
That means we use less space on the stack, because we don't have to decrease the stack pointer to fit more data.