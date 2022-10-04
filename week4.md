# Assigment 4
**EAS503**

1. We covered list and dictionary comprehension. There are three variations of list/dictionary comprehension: no conditional, if conditional, and if/else conditional. Give simple examples where you do not use list/dictionary comprehension and then repeat the same examples with list/dictionary comprehension. There will be 12 examples in total -- 3 plain list example, 3 list comprehension examples, 3 plain dictionary examples, and 3 dictionary comprehensions examples.

    List
    Re-write the plain list example 1 to use list comprehension ex 1
    ```
    my_list = [1, 2, 3]
    new_list = []
    for ele in my_list:
        tmp = ele * ele
        new_list.append(tmp)
        
    new_list = [ele*ele for ele in my_list]
    ```
    Re-write the plain list if/else example 2 to use list comprehension ex 2
    ```
    ret = []
    numbers = range(10)
    for number in numbers:
        if number % 2 == 0:
            ret.append(number)
        else:
            ret.append(number**3)
    
    numbers = range(10)
    ret = [number if number % 2 == 0 else number**3 for number in range(10)]
    ```
    Re-write the plain list if example 3 to use list comprehension ex 3
    ```
    numbers = range(20)
    even = []
    odd = []
    for number in numbers:
        if number % 2 == 0:
            even.append(number)
        if number % 2 != 0:
            odd.append(number)
    
    numbers = range(20)
    even = [number for number in numbers if number % 2 == 0 ]
    odd = [number for number in numbers if number % 2 != 0 ]
    ```
    
    Dictionaries
    Re-write the plain dictionary example 1 to use dictionary comprehension ex 1  
    ```
    list1 = ['john', 'jane', 'doe']
    list2 = [95, 99, 98]
    dict = {}
    for i in range(len(list1)):
        dict [list1[i]] =  list2[i]
    
    list1 = ['john', 'jane', 'doe']
    list2 = [95, 99, 98]
    dict = {list1[i]: list2[i] for i in range(len(list1))}
    ```
    Re-write the plain dictionary if/else example 2 to use dictionary comprehension ex 2  
    ```
    dict = {}
    for num in range(1, 20):
        if num % 2 == 0:
            dict[num] = "even"
        else:
            dict[num] = "odd"
    
    dict = {num: ("even" if num % 2 == 0 else "odd") for num in range(1, 20)}
    ```
    Re-write the plain dictionary if example 3 to use dictionary comprehension ex 3
    ```
    dict = {}
    for num in range(1, 20):
        if num % 2 == 0:
            dict[num] = "even"
    
    dict = {num:"even" for num in range(1, 20) if num % 2 == 0 }
    ```
    
2. A student comes to you and says that they used Python to simulate 10 coin tosses and got observed 7 heads and 3 tails. They tell you that something is wrong with Python. Are they correct? Explain in detail.

     No, the students are not correct. The python's randomization functionalities are proven to achieve true randomness, hence each coin flip can ensure realistic probability. The coin tosses outcome are not acvaheing ~50% because that simulation was run 10 times. If it was run for more generations it can achieve closer and closer to absolute 50%.

3. Explain the purpose of continue and break in looping.

    Continue will skip this current iteration and break will exit the loop at all. We can use continue if we need to filter a list we can use break if we want to exit upon reaching a condition.

4. Assume there is a csv file whose first line is the column headers and the rest of the rows are values. How can you use zip to create a list in which each element is a dictionary whose keys are the column headers and values are the values from the rows? Hint: I am asking you to basically explain the following code that we covered in lecture.
    ```
    filename = 'people.csv'
    
    students = []
    header = None
    with open(filename) as file:
        for line in file:
            if not line.strip():
                continue
                
            if not header:
                header = line.strip().split('\t')
                continue
    #         print(header)
    #         print(line.strip().split('\t'))
    #         print(dict(list(zip(header, line.strip().split('\t')))))
    #         tmp = dict(zip(header,line.strip().split('\t')))
            students.append(dict(zip(header,line.strip().split('\t'))))
    for student in students:
        print(student)
    ```
    Below is the corrected version of the code:    
    ```
    filename = 'ppl.csv'
    
    students = []
    header = None
    with open(filename) as file:
        for line in file:
            if not line.strip():
                continue
                
            if not header:
                header = line.strip().split('\t')
                continue
    
            students.append(dict(zip(header[0].split(','),line.strip().split(','))))
          
    for student in students:
        print(student)
    ```
    Below is the files:
    ```
    CSV file:
    A,B,C,D
    1,2,3,4
    0,1,0,1
    
    Output:
    >>>{'A': '1', 'B': '2', 'C': '3', 'D': '4'}
    >>>{'A': '0', 'B': '1', 'C': '0', 'D': '1'}
    ```
    
