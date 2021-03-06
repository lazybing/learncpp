In summary, you should prefer a deque if the following are true:
1. You insert and remove elements at both ends(this is the classic case for a queue).
2. You don't refer to elements of the container.
3. It is important that the container frees memory when it is no longer used.

**Deque Operations**

| Operations | Effect |
| :-----:   | :----: |
|deque<Elem> c;          | Default constructor;creates an empty deque without any elements |
|deque<Elem> c(c2);      | Copy constructor; creates a new deque as a copy of c2 |
|deque<Elem> c = c2;     | Copy constructor; creates a new deque as a copy of c2 |
|deque<Elem> c(n);       | Creates a deque with n elements created by the default constructor |
|deque<Elem> c(n, elem); | Creates a deque initialized with n copies of element elem |
|deque<Elem> c(beg, end);| Creates a deque initialized with the elements of the range [beg, end) |
|deque<Elem> c(initlist);    | Creates a deque initialized with the elements of the initializer list initlist |
|deque<Elem> c = initlist;   | Creates a deque initialized with the elements of the initializer list initlist |
|c.~deque();                 | Destroys all elements and frees the memory

| Operations | Effect |
| :-----:   | :----: |
| c.empty();          | Returns whether the container is empty |
| c.size();           | Returns the current number of elements |
| c.max_size();       | Returns the maximum number of elements possible |
| c1 == c2;           | Returns whether c1 is equal to c2 |
| c1 != c2;           | Returns whether c1 is not equal to c2 |
| c1 < c2;            | Returns whether c1 is less than c2 |
| c1 > c2;            | Returns whether c1 is greater than c2 |
| c1 <= c2;           | Returns whether c1 is less than or equal to c2 |
| c1 >= c2;           | Returns whether c1 is greater than or equal to c2 |
| c[idx];             | Returns the element with index idx |
| c.at(idx);          | Returns the element with index idx(throws range-error exception if idx is out of range) |
| c.front();          | Returns the first element |
| c.back();           | Returns the last element |
| c.begin();          | Returns a random-access iterator for the first element |
| c.end();            | Returns a random-access iterator for the position after the last element |
| c.cbegin();         | Returns a constant random-access iterator for the first element |
| c.cend();           | Returns a constant random-access iterator for the position after the last element |

| Operations | Effect |
| :-----:   | :----: |
| c = c2;             | Assigns all elements of c2 to c |
| c = initlist;       | Assigns all elements of the initializer list initlist to c |
| c.assign(n, elem);  | Assigns n copies of element elem |
| c.assign(beg, end); | Assigns the elements of the range [beg, end) |
| c.assign(initlist); | Assigns all the elements of the initializer list initlist |
| c1.swap(c2);        | Swaps the data of c1 and c2 |
| c.push_back(elem);  | Appends a copy of elem at the end |
| c.pop_back();       | Removes the last element(does not return it) |
| c.push_front(elem); | Inserts a copy of elem at the beginning |
| c.pop_front();      | Removes the first element(does not return it) |
| c.insert(pos, elem);| Inserts a copy of elem before iterator position pos and returns the position of the new element |
| c.insert(pos, n, elem); | Inserts n copies of elem before iterator position pos and returns the position of the first new element |
| c.insert(pos, beg, end);| Inserts a copy of all elements of the range [beg, end) before iterator position pos and returns the position of the first new element |
| c.insert(pos, initlist);| Inserts a copy of all elements of the initializer list initlist before iterator position pos and returns the position of the first new element |
| c.erase(pos);           | Removes the element at iterator position pos and returns the position of the next element |
| c.erase(beg, end);      | Removew all elements of the range [beg, end) and returns the position of the next element |
| c.resize(num);          | Changes the number of elements to num |
| c.clear();              | Removes all elements |

