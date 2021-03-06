If you need a sequence with a fixed number of elements, class array<> has the 
best performance because memory is allocated on the stack (if possible), reallocation
never happens, and you have random access.

1. Initialization

Note that array<> is the only container whose elements are default initialized when nothing
is passed to initialize the elements. This means that for fundamental types, the initial
value might be undefined rather than zero.

```
std::array<int, 4> x;       //OOPS:elements of x have undefined value
std::array<int, 4> x = {};  //OK:all elements of x have value 0
std::array<int, 5> coll = {42, 377, 611, 21, 44};
std::array<int, 10> c2 = {42};  //one element with value 42
                                //followed by 9 elements with value 0
std::array<int, 5> c3 = {1, 2, 3, 4, 5, 6}; //ERROR: too many values
```

You can't use the parenthesis syntax to specify initial values(which differs
                                                from other container types:)
```
std::array<int, 5> a({1, 2, 3, 4, 5, 6});   //ERROR
std::vector<int> v({1, 2, 3, 4, 5, 6});      //ERROR
```

2. swap() and move semantics

```
std::array<std::string, 10> as1, as2;
...
as1 = std::move(as2);
```

3. Size

```
std::array<Elem, 0> coll;   //array with no elements
std::sort(coll.begin(), coll.end());    //OK(but has no effect)
coll[5] = elem;                         //RUNTIME ERROR ==> undefined behavior
std::cout << coll.front();              //RUNTIME ERROR ==> undefined behavior
```

4. Array Operations

**Create/Copy/Destroy**

| Operations | Effect |
| :-------:  | :---:  |
| array<Elem, N> c        | Default constructor; creates an array with default-initialized elements |
| array<Elem, N> c(c2)    | Copy constructor; creates a copy of another array of the same type |
| array<Elem, N> c = c2   | Copy constructor; creates a copy of another array of the same type |
| array<Elem, N> c = initlist | Creates an array initialized with the elements of the initializer list |

**Nonmodifying Operations**

| Operations | Effect |
| :-------:  | :---:  |
|c.empty()               | Returns whether the container is empty |
|c.size()                | Returns the current number of elements |
|c.max_size()            | Returns the maximum number of elements possible |
|c1 == c2                | Returns whether c1 is equal to c2 |
|c1 != c2                | Returns whether c1 is not equal to c2 |
|c1 < c2                 | Returns whether c1 is less than c2 |
|c1 > c2                 | Returns whether c1 is greater than c2 |
|c1 <= c2                | Returns whether c1 is less than or equal to c2 |
|c1 >= c2                | Returns whether c1 is greater than or equal to c2 |

**Assignments**

| Operations | Effect |
| :-------:  | :---:  |
| c = c2          | Assigns all elements of c2 to c |
| c = rv          | Move assigns all elements of the rvalue rv to c |
| c.fill(val)     | Assigns val to each element in array c |
| c1.swap(c2)     | Swaps the data of c1 and c2 |
| swap(c1, c2)    | Swaps the data of c1 and c2 |

**Element Access(only at() performs range checking.)**

| Operations | Effect |
| :-------:  | :---:  |
| c[idx]          | Returns the element with index idx |
| c.at(idx)       | Returns the element with index idx(throws range-error exception if idx is out of range) |
| c.front()       | Returns the first element(no check whether a first element exists) |
| c.back()        | Returns the last element(no check whether a last element exists) |

**Iterator Functions**

| Operations | Effect |
| :-------:  | :---:  |
| c.begin()       | Returns a random-access iterator for the first element |
| c.end()         | Returns a random-access iterator for the position after the last element |
| c.cbegin()      | Returns a constant random-access iterator for the first element |
| c.cend()        | Returns a constant random-access iterator for the position after the last element |

