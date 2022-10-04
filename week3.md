# Assigment 3 
**EAS503**

## List Review
1. Can the elements in a list in Python contain different data types or only one data type?

    Yes, for example x = [40, "40", [20]] is valid, that list contains 3 data types.

2. When will the max, min, and sum function work on a list and when will they not work?

    The  max, min, and sum function will work on a list if the list contians all ints or floats, it will throw a type error if the list contians other types. For ex:
    ```
    >>> max([4,5,6555.3333,222])
    6555.3333
    >>> max([4,5,6555.3333,"good"])
    Traceback (most recent call last):
        File "<stdin>", line 1, in <module>
    TypeError: '>' not supported between instances of 'str' and 'float'
    ```

3. How do the all and any functions work?

    The any and all functions in py returns either true or false. They take in in a list and dict of comparisons or boolean. The any function will return the true if any element in the list is true or key in the dict. The all function will do the same except that all elements must be true for the funtion to return true.

4. How do you access a particular element in a list? What does it mean that lists in Python are 0-indexed?

    List index are the placement ordeing of elements in a list, element at index 0 are placed in the first place of the list, index 1 at 2nd place and so on. 0-indexed means the index in a py list starts at 0.

5. Explain what list slicing is? Hint: explain start index, end index, and step size. Give some examples to clarify this concept. Make sure to explain how the colon works. You can have start index and no end index; you can have end index, but no start index; you can have both start and end index; you can have no start index, but end index and step size.
    ```
    >>> grades = ['A', 'B', 'C', 'D', 'F']
    >>> grades[2:4]
    ['C', 'D']
    >>> grades[1::2]
    ['B', 'D']
    >>> grades[-1]
    'F'
    >>> grades[::-1]
    ['F', 'D', 'C', 'B', 'A']
    >>> grades[:2]
    ['A', 'B']
    >>> grades[2:]
    ['C', 'D', 'F']
    ```
    [x:y]- x is the start index and y is the end index. The x and y is like a frame where the list is going to be cut. [x::y]- x is the index to start from and y is the step size.
    
6. What does index -1 mean? How can you reverse a list using it?

    The index -1 mean the last item in the list, -1 to -n will traverse the list backwards. For example [4,5,-3][-1] would be -3. We can use this method to reverse a list. We can do list[::-1] to make it reverse.

7. What are two ways of deleting an element from a list at a particular index?

    In python .pop(n), n is the index we wish to remove. Or we can use the .remove(x) function, x will be the element in the list and the first occurance of it will be deleted.

8. What is the meaning of the + operator when the operands are a list?

    This operator is to combine 2 list, it adds the elements of the left hand and the elements in the right hand into one list keeping the respective order.

9. What is the meaning of the * operator on a list? Give an example of how you can use it?

    The "*" operator can replicate the left hand side list, it will repeat the left hand side list by the number on the right hand side, and combine it into one list. For example:
    ```
    >>> [1]*4
    [1, 1, 1, 1]
    ```

10. What is the difference between sort and sorted?

    sorted can sort dict and list and sets and returns sorted list. The .sort is a method of the list classes and it is a in place operation where it modifies the original sequence in place.

11. Will the index method on a list return all the indices where the specified value occurs?

    No, it will only return the first index in a list that matches the inputted value.
    For example, [2, 4, 5, 2].index(2) will return 0.

12. What method can you use to remove the last element from a list and also get that value?

    [...].pop(-1), the pop method with -1 index. For example, [4,5,-3].pop(-1) will return -3.

13. Is it possible to modify a tuple?

    Tuples are immutable, once a tuple is created it cant be modified again.

14. What operator can be used to check if an element exists inside a sequence?

    We can use the "in" operator, this is the main and usual way of doing it. If we cant use this operator due to limitations then we can use .count() and check if there are occurances of the element in the sequence.
    
15. What is the significance of calling a list and string a sequence?

    List is a sequence and as well as a string, list can be accessed by index so can a string. A string is a sequence of characters, strings can be seen as a list of chars.

## For Loop Review
1. Explain how the range function works. Hint explain when 1, 2, and 3 inputs arguments are provided. Also explain how to get or see the actual values as a list?

    The range(n) will generate a sequence from 0 to n-1, range(x,n) will generate a sequence from x to n-1. Lastly range(x,n,z) will generate a sequence from x to n-1 but will skip z-1 iterations, or in other words iterate every zth iteration. 
    Make range(20) to a list by doing, list(range(20)).

2. If you want to loop over a list using indices, how can you do that? Show sample code.
    ```
    lst = [1,3,4,"hello","WORLD!"]
    for i in range(len(lst)):
        iteration = lst[i]
    ```
    
3. Explain what the enumerate function does? Hint: make sure to explain how you can change the start index. Show some sample codes.

    Enumerate returns the iteration count and the element value in that iteration, it is a helper function.
    ```
    values = [4, 10, 3, 8, -6]
    for index, value in enumerate(values):
        print(index, value)
    ```
4. If you want to simultaneously access two or more lists at the same time in Python, how can you do it? We covered two ways of doing this.
    ```
    metals = ['Li', 'Na', 'K']
    weights = [6.941, 22.98976928, 39.0983]
    for metal, weight in zip(metals, weights):
        print(metal, weight)
    ```
    We can use the zip function to iterate many list at the sametime.
    ```
    metals = ['Li', 'Na', 'K']
    weights = [6.941, 22.98976928, 39.0983]
    for i in range(len(metals)):
        print(metals[i], weights[i])
    ```
    We can use the len and range function to iterate many list at the sametime by using the index, but you must make sure to use the lesser index or else there will be a index over.
    
5. Explain the zip function. How many lists can you zip up? What happens when there is a length mismatch between lists?

    The zip function will return a sequence of tuples which holds the corresponding elements all the list at each index. If there is a length mismatch the the function will chop off the longer part.

6. When you split a string on some character, what data type will be returned? Give examples of when it is useful to split a string?

    When you split a string a list will be returned with the whole string as mutiple elements in the list. When you are given a date in string such as "90/19/1963" and you need the dates separately.
    ```
    print("09/19/1963".split("/"))
    >> ["09","19","1963"]
    ```
7. Say you are parsing a text file with many lines of data. You know that there should always be five columns in each line. Explain how you can verify the integrity of this file? Give an example of when there could be more columns than expected?

    We can use a csv reader or use a split method. Always double check the columns by counting it or printing it out. If parsing of the commas are done wrong then a string with a "," could be split as an additional column.  
    ```
    "a,b,c,d,'10,000'".split(",")
    ["a","b","c","d","'10","000'"]
    ```
8. Sometimes before the for loop code you have initialize a variable to 0 or an empty list. Why do you have to do this? Give some examples to explain how the variable would be used inside a loop to explain this.

    This is called the accumulator pattern, we do this when we loop over data and we need to extract some values or a statistics to bring outside of the loop.
    ```
    def pow(input_list, power):
        output = []
    
        for ele in input_list:
            output.append(ele ** power)
    
        return output
    ```
    
        Just from looking at this, we know output is a list holder that will be returned holding values of some kind from the for loop iterations.

9. Explain in detail the purpose of the following lines using an example.if not line.strip():
    ```
    if not line.strip():
    continue
    ```
    If line.strip() is empty, or there is nothing in the actual string other than empty spaces, skip this iteration in the code.
    
10. Explain in detail the purpose of the following lines using an example.
    ```
    try:
        value = float(line)
    except:
        continue
    ```
    This code will try to convert variable line to a float if there is a error exception then the code will just move on with this iteration disregarding the conversion.


