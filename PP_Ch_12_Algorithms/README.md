# PP_Ch_12_Algorithms



```python 
from typing import List, Tuple

def find_two_smallest(L: List[float]) -> Tuple[int, int]:
    """Return a tuple of the indices of the two smallest values in list L.

    >>> items = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    >>> find_two_smallest(items)
    (6, 7)
    >>> items == [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    True
    """
    # Find the index of the minimum item in L
    # Remove that item from the list
    # Find the index of the new minimum item in the list
    # Put the smallest item back in the list
    # If necessary, adjust the second index
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Get the minimum item in L            <-- This line is new
    # Find the index of that minimum item  <-- This line is new
    # Remove that item from the list
    # Find the index of the new minimum item in the list
    # Put the smallest item back in the list
    # If necessary, adjust the second index
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Find the index of the minimum and remove that item
    smallest = min(L)
    min1 = L.index(smallest)
    L.remove(smallest)

    # Find the index of the new minimum
    next_smallest = min(L)
    min2 = L.index(next_smallest)

    # Put the smallest item back in the list
    # If necessary, adjust the second index
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Find the index of the minimum and remove that item
    smallest = min(L)
    min1 = L.index(smallest)
    L.remove(smallest)

    # Find the index of the new minimum
    next_smallest = min(L)
    min2 = L.index(next_smallest)

    # Put smallest back into L
    # Fix min2 in case it was affected by the removal and reinsertion:
    # If min1 comes before min2, add 1 to min2
    # Return the two indices

``` 

```python 
from typing import List, Tuple

def find_two_smallest(L: List[float]) -> Tuple[int, int]:
    """Return a tuple of the indices of the two smallest values in list L.

    >>> items = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    >>> find_two_smallest(items)
    (6, 7)
    >>> items == [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    True
    """

    # Find the index of the minimum and remove that item
    smallest = min(L)
    min1 = L.index(smallest)
    L.remove(smallest)

    # Find the index of the new minimum
    next_smallest = min(L)
    min2 = L.index(next_smallest)

    # Put smallest back into L
    L.insert(min1, smallest)

    # Fix min2 in case it was affected by the removal and reinsertion:
    if min1 <= min2:
        min2 += 1

    return (min1, min2)

``` 

```python 
[6.4, 6.3, 7.5, 8.5, 9.4, 12.3, 13.1, 13.2, 11.8, 9.4, 9.5, 5.8, 7.3, 6.6, 9.2, 8.4, 10.5, 12.4, 13, 11.7, 11.9, 10.2, 7.2, 6.9, 7.3, 7.6, 7.5, 11, 11.2, 12.4, 13.2, 12.6, 12, 10.9, 9, 7.4, 7.3, 6.4, 8.4, 10.5, 12.7, 13.4, 14.1, 13.2, 13.1, 12.6, 11.1, 7, 7.9, 5.8, 8.4, 9.3, 10.3, 12.3, 11.7, 11.1, 10.7, 9.7, 8.1, 4.4, 5.6, 4.8, 7.1, 8.6, 10.8, 12.5, 13.6, 12.6, 12.1, 11, 9.4, 8, 5.5, 6.9, 9.7, 10.4, 11.2, 13.1, 13.7, 13.4, 12.6, 12, 9.9, 8.8, 9, 8.4, 10.2, 10.1, 11.1, 11.1, 12.8, 13, 10.9, 10.2, 5.8, 4.4, 4.1, 6.3, 6.8, 8.6, 10.8, 11.3, 12.6, 12.2, 10.6, 9.7, 9.2, 7.5, 5.3, 6.8, 9.2, 10, 12.2, 13.1, 14.2, 14.7, 13.7, 11.4, 10.1, 8.9, 6.5, 8.1, 5.9, 9.8, 11.7, 11.9, 13, 12.2, 11.2, 9.2, 8, 7.2, 5.7, 5.6, 8.8, 9.1, 11.1, 11.8, 12.2, 13, 11.6, 9.6, 8.6, 7.8, 3.5, 6.1, 7.5, 9.4, 11.7, 12.7, 13.8, 12.4, 12, 10.8, 9, 7.7, 5.5, 7.1, 8.4, 10, 12.2, 12.8, 12.9, 12.6, 11.7, 10.8, 10.8, 7.7, 6.2, 6.2, 7.8, 9.2, 13.7, 13.3, 13.5, 14.8, 13.6, 12.9, 10.1, 9.6, 7.6, 7.3, 9.8, 10.8, 12.7, 12.6, 13.7, 13, 11.7, 10.7, 9.1, 5.7, 6.1, 5.2, 4, 9.2, 11.5, 12.1, 13.1, 12.5, 10.7, 9.6, 6.9, 6.2, 5.5, 7.3, 6.2, 9.3, 11.4, 13, 13.5, 12.8, 12.5, 11.8, 9.8, 8.1, 7.7, 8.1, 9.9, 10.8, 11.5, 12, 12.1, 11.2, 11.4, 10.6, 9.1, 8.4, 6.5, 6.8, 7.4, 9.8, 11.5, 12.2, 13.2, 13.1, 12.8, 10.5, 9.9, 7.4, 5.8, 8.1, 8.1, 10.3, 12.8, 13.1, 14, 13.4, 13.4, 12.2, 10.9, 8.4, 8.1, 8.6, 5.9, 9, 11, 12.8, 11.6, 12.8, 11.2, 10, 8.4, 5.4, 5.9, 5.5, 7.1, 7.6, 10.8, 13.3, 13.3, 13.2, 12, 9.9, 10.1, 7.9, 7.7, 7.9, 10.7, 10.7, 11.1, 12.7, 13.7, 13.6, 11.8, 10.3, 10.8, 8.6, 6.5, 7.2, 8.6, 10, 11.1, 12.1, 12, 12.5, 10.5, 9.8, 7.2, 6.8, 5, 6.2, 8, 9.8, 11.4, 11.6, 12.4, 12.8, 12.1, 10.6, 8.7, 5.9, 7.7, 5.6, 7.3, 8.1, 11.2, 12.9, 13, 12.4, 11.7, 10.2, 8.4, 6.9, 5.6, 7.6, 5.8, 9.7, 10.5, 11.6, 12.1, 11.9, 11.2, 9.6, 8.3, 6.7, 4.4, 5, 6.8, 8.2, 11.1, 11.1, 11.8, 11.8, 10.6, 10.6, 7.1, 5.7, 5.5, 5.6, 7.8, 8.6, 11.8, 14, 13.5, 13.4, 12.1, 12, 9.9, 7.6, 7.6, 9, 8.1, 11.7, 12.4, 12.4, 12, 13.3, 11.2, 11, 8.8, 8.6, 6, 7, 6.9, 9.6, 12.4, 13.3, 13.9, 13, 13.3, 11.9, 10.1, 8.1, 8.5, 8.5, 7.5, 10.3, 11.1, 13.4, 14.4, 14.7, 13.4, 13.4, 10.7, 8.6, 8.6, 7.7, 10.6, 11.3, 11.7, 11.7, 12, 12.6, 10.5, 9.9, 8.5, 5.4, 5.2, 5.9, 7.6, 9.8, 9.9, 10.4, 11.2, 12.3, 10.8, 9, 7.7, 4.2, 6.1, 7.3, 5.8, 8.5, 10.5, 11.1, 11, 10.9, 10.4, 9.7, 7.4, 5.1, 5.5, 5.4, 8.9, 9, 10.7, 12.4, 14, 13.5, 14.1, 11.2, 9.2, 8, 7.2, 8.8, 8.5, 9.4, 10.9, 12.9, 13.2, 13.7, 12.3, 11.2, 9.8, 8.1, 5.1, 6.9, 8.9, 8.9, 10.8, 10.2, 11.2, 12, 11, 10.2, 8.4, 5.5, 4.9, 6.5, 6.7, 10, 10, 10.6, 12.1, 13.1, 12, 10.4, 8.9, 6.2, 5.5, 5.1, 6.8, 9.4, 10.6, 11.6, 12.6, 12.9, 11.5, 10.6, 8.7, 6.2, 5.1, 6.5, 6.4, 8.1, 10.2, 11.6, 13.9, 14.6, 12.4, 11.4, 9.5, 7, 7.4, 6.8, 7.3, 9.4, 10.5, 12.3, 13.2, 12.8, 12, 9.5, 8, 5.8, 5.4, 3.9, 5.2, 7.9, 10.5, 12.1, 13.9, 12.8, 12.8, 11.6, 10.3, 8.3, 6.5, 8.5, 9.4, 10.2, 11.1, 12.8, 12.9, 12.9, 11.4, 9.8, 9.5, 6.5, 5.1, 6.9, 6.8, 8.6, 10.7, 11.8, 12.4, 13.3, 12.4, 11.2, 9.5, 7.1, 8.3, 5.8, 6.5, 9, 11.9, 12.8, 12.7, 13.2, 11.7, 9.3, 9.6, 6.3, 3.1, 4.3, 7.4, 9.5, 11.9, 13.4, 13.7, 13.2, 12.5, 10.8, 8, 6.3, 4.8, 6.6, 8.2, 10, 12, 12.9, 13.5, 13.6, 13.2, 11.7, 10.8, 7.9, 6.3, 8.3, 8.6, 9.4, 11.4, 12.7, 13.2, 12.5, 11.2, 11.4, 8.9, 6.8, 5.3, 7.4, 7.9, 10.2, 11, 12.5, 13.5, 13.5, 11.7, 10.2, 9, 6.4, 6.8, 5.5, 6.7, 9.5, 11.2, 12.5, 13, 13.3, 11.7, 9.8, 8.1, 6.4, 5.9, 7.3, 7, 8.8, 11.4, 11.7, 12.5, 13.6, 12.2, 10.9, 8.6, 7.4, 5.4, 7.4, 6, 9.4, 12, 12.8, 12.7, 13.5, 10.8, 9.7, 9.2, 8.1, 6.7, 6.9, 7.6, 9.1, 10.1, 12.6, 12.5, 12.1, 11.6, 10.7, 9.4, 6.8, 5.2, 7.8, 6, 9.2, 12, 12.2, 13.4, 12.6, 12.5, 10.9, 8.3, 6.5, 5.2, 5.6, 8, 9, 9.8, 11.4, 11.8, 11.7, 11.7, 10.7, 7.8, 6.8, 4.8, 5.9, 6.5, 9.1, 11.2, 12.4, 12.8, 11.6, 13.3, 11.6, 9.2, 9.2, 5.7, 6.5, 8.7, 10.7, 12.2, 14, 14.3, 14.1, 14.1, 13.8, 9.6, 9.9, 7.8, 9.7, 8.7, 10.6, 11.2, 13.7, 15.4, 14.5, 12.7, 11.9, 9.2, 8.8, 8.5, 6.3, 8.6, 10.3, 9.8, 11.8, 13.2, 12.1, 11.1, 9.5, 8.3, 6.7, 6.3, 4.9, 7.4, 8.8, 10.8, 13.1, 12.6, 12, 11.1, 9.7, 8.4, 7.7, 7.2, 6.7, 7.6, 10.2, 11.6, 13.1, 14, 13.5, 12.4, 11.3, 9, 6.3, 6.5, 6.4, 5.8, 10.3, 11.3, 11.8, 13.4, 12.2, 11.9, 11.1, 9.3, 7.2, 6.3, 5.5, 8.6, 10.4, 11.6, 13.2, 13.8, 13.4, 12.7, 11.8, 9.2, 7.3, 7.5, 6.3, 7, 9.6, 12.4, 12.6, 13.2, 11.6, 11.5, 10.6, 8.2, 6.7, 7.3, 6.5, 7.6, 9, 10.8, 12.7, 12.3, 12.2, 12.2, 10.4, 7.6, 7.7, 7.3, 5.6, 6.2, 10.1, 11.1, 13.5, 13, 13.4, 11.8, 9.8, 9, 5.2, 4.7, 4.3, 6.5, 7.7, 9.9, 10.7, 12.1, 12, 11.7, 9.5, 6.5, 4.4, 5.3, 5.1, 7, 9.4, 11.9, 11.2, 13.3, 13.2, 12.5, 11.4, 9.5, 8.9, 6.7, 7.1, 8.3, 10.3, 10.3, 12.5, 13, 12.6, 12.1, 9.9, 7.7, 8.4, 6.9, 7.3, 8, 8.9, 13.1, 12.5, 13.9, 13, 13.2, 10.8, 9.4, 8.1, 4.9, 7.3, 7.7, 7.7, 10.1, 12.3, 12.4, 11.8, 11.9, 10.7, 9.1, 6.5, 8.3, 3.7, 6.7, 8.9, 9.4, 10.9, 11.7, 11.4, 10.9, 9.3, 7.6, 7.6, 4.8, 4.7, 6.9, 8.3, 9.1, 11.3, 11.2, 11.5, 11.4, 9.7, 8.7, 5.6, 6.5, 6.4, 7.8, 9.5, 12.3, 12.5, 12.9, 13.3, 13.1, 11.5, 9.8, 7.7, 8.5, 7.1, 8.1, 8.9, 10.9, 11.6, 12.4, 11.6, 11.5, 9.6, 9.1, 8.3, 6.1, 8.7, 6.9, 8.9, 10.4, 12.8, 13.5, 13.1, 11.9, 10.5, 7.7, 6.1, 6.5, 6.7, 7.1, 8.5, 10, 12.5, 12.5, 12.5, 10.5, 10.7, 8.7, 7.2, 7.2, 6.4, 9.6, 9.2, 11.1, 12.8, 13.1, 13.2, 12.1, 10.4, 9.2, 6.7, 5.1, 7.4, 8.4, 9.8, 10.1, 11.5, 12.3, 13.3, 11.1, 9.7, 8.1, 7.3, 5.9, 8, 6.7, 8.5, 10.3, 13.3, 13.5, 12.4, 12.7, 12.4, 10.3, 9, 7.3, 7.1, 7, 9.1, 10.5, 11.8, 12, 12.1, 10.4, 9.5, 7.8, 7.6, 6.3, 5.7, 6.9, 11.2, 11.2, 14, 15.5, 13.7, 13.3, 12.4, 10.4, 6.6, 7.5, 6.7, 8.6, 9.9, 12.3, 13.3, 12.9, 12.6, 12.1, 11.3, 8.9, 7.6, 5, 5.6, 7.2, 10.7, 11, 12.5, 12.8, 12.8, 12.7, 10.8, 8.9, 7.8, 4.1, 5.1, 8.2, 9.7, 9.5, 12.2, 12.7, 12.7, 12.2, 11, 9.8, 7.3, 5.8, 6.3, 8.3, 10.9, 11, 12.7, 13.5, 13.4, 11.8, 11.5, 9.1, 6.9, 8.2, 7.2, 7.2, 10, 10.6, 11.8, 13.8, 12, 10.1, 8.7, 7.5, 5.2, 5.8, 4.5, 6, 8, 10.4, 13, 12.5, 11.7, 10.8, 9.5, 8.3, 5.8, 5.8, 5.1, 6.7, 10.6, 13.7, 12.8, 13.8, 13.8, 13.7, 12.6, 9.8, 9.6, 7.3, 8.3, 7, 9, 10.8, 11, 12.4, 11.5, 11.4, 10, 5.7, 6.6, 4, 4.4, 5.5, 8.8, 11, 12.4, 12.6, 12.1, 11, 9.6, 7.7, 6.1, 6.4, 6.9, 6.6, 7.8, 10.4, 11.4, 11.7, 11.3, 10.4, 8.9, 8, 5.5, 5.1, 5.4, 5.6, 9.9, 12, 12.6, 14, 14.1, 12.9, 9.9, 7.8, 6.5, 5.9, 5.6, 8.1, 9.3, 11.3, 13.5, 13.6, 13.6, 12.9, 12.3, 10, 8.1, 8.2, 8.9, 9.5, 10.1, 9.3, 11.1, 11.3, 11.9, 11.6, 10.7, 9.1, 7.4, 6, 6.9, 7.9, 9.7, 11.2, 12.6, 11.1, 13.3, 11.7, 11, 9.1, 8.5, 5.9, 6.3, 7.2, 9.7, 11.3, 12.5, 13.2, 13.4, 12.7, 10.7, 9.1, 7.3, 5.1, 6.2, 9.9, 9.9, 10.5, 11.5, 11.8, 12.4, 11.5, 11.1, 8.4, 7.5, 6.3, 7, 7.5, 10.1, 11.9, 13.9, 14.5, 14.7, 14, 12.5, 11.1, 9.3, 9.8, 10.3, 10.1, 10.1, 11.7, 13.3, 14.4, 14.1, 12.1, 10.5, 9.7, 8.5, 7.1, 5.3, 8.1, 10.1, 11.1, 13.2, 13.2, 12.2, 11.8, 11.3, 9.3, 5.1, 7.5, 5.4, 6.1, 7.5, 9.4, 12.6, 13.6, 12.4, 11.5, 10.7, 8.4, 7.6, 4.7, 6.9, 8.4, 9.3, 11.6, 11, 12.8, 12, 12.2, 10.9, 9.3, 9.7, 7.1, 7.4, 10.7, 11.5, 12.6, 13.1, 14.7, 14.3, 13.5, 11.2, 8.9, 7.8, 7.8, 6.7, 6.8, 10.1, 10.8, 13.9, 12.8, 12.5, 10.6, 9.1, 7.4, 6.5, 5.4, 6.8, 7.3, 7.6, 10.1, 12.8, 12.1, 13.3, 11.7, 9.9, 8.7, 8.9, 6.9, 10, 8.3, 9.7, 10.3, 12.4, 12.8, 13.5, 13.3, 10.9, 9.1, 7.7, 6.3, 6.5, 9.5, 9.9, 12.6, 13.3, 13.4, 14, 13.3, 11.1, 10.1, 8.5, 10.1, 7.7, 10.5, 11, 11.1, 12.5, 14.9, 12.8, 11.2, 11.2, 9.5, 7.3, 6.8, 6.4, 10.1, 11.4, 12.4, 13.9, 13.5, 15.1, 13.4, 12, 9, 7, 6.7, 6.5, 9.4, 10.8, 12, 12.9, 14.1, 14.9, 13.5, 11.9, 9.8, 9.3, 7, 7.8, 7.2, 9.6, 11.6, 13, 12.7, 13.2, 12, 10.2, 8.8, 7.5, 5.7, 6.2, 7.4, 9, 12.2, 12.4, 12.5, 12.4, 10.3, 9.7, 8.4, 5.6, 7.3, 4.8, 8.6, 11.9, 11.9, 14.7, 14.3, 15.1, 14.7, 13.4, 11.4, 8.6, 7.8, 10.2, 10, 11.1, 11.5, 12.1, 12.6, 12.7]
``` 

```python 
>>> counts = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
>>> min(counts)
96

``` 

```python 
>>> counts = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
>>> low = min(counts)
>>> counts.index(low)
6

``` 

```python 
>>> counts = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
>>> counts.index(min(counts))
6

``` 

```python 
6.4
6.3
7.5
8.5
9.4
12.3
13.1
13.2
11.8
9.4
9.5
5.8
7.3
6.6
9.2
8.4
10.5
12.4
13
11.7
11.9
10.2
7.2
6.9
7.3
7.6
7.5
11
11.2
12.4
13.2
12.6
12
10.9
9
7.4
7.3
6.4
8.4
10.5
12.7
13.4
14.1
13.2
13.1
12.6
11.1
7
7.9
5.8
8.4
9.3
10.3
12.3
11.7
11.1
10.7
9.7
8.1
4.4
5.6
4.8
7.1
8.6
10.8
12.5
13.6
12.6
12.1
11
9.4
8
5.5
6.9
9.7
10.4
11.2
13.1
13.7
13.4
12.6
12
9.9
8.8
9
8.4
10.2
10.1
11.1
11.1
12.8
13
10.9
10.2
5.8
4.4
4.1
6.3
6.8
8.6
10.8
11.3
12.6
12.2
10.6
9.7
9.2
7.5
5.3
6.8
9.2
10
12.2
13.1
14.2
14.7
13.7
11.4
10.1
8.9
6.5
8.1
5.9
9.8
11.7
11.9
13
12.2
11.2
9.2
8
7.2
5.7
5.6
8.8
9.1
11.1
11.8
12.2
13
11.6
9.6
8.6
7.8
3.5
6.1
7.5
9.4
11.7
12.7
13.8
12.4
12
10.8
9
7.7
5.5
7.1
8.4
10
12.2
12.8
12.9
12.6
11.7
10.8
10.8
7.7
6.2
6.2
7.8
9.2
13.7
13.3
13.5
14.8
13.6
12.9
10.1
9.6
7.6
7.3
9.8
10.8
12.7
12.6
13.7
13
11.7
10.7
9.1
5.7
6.1
5.2
4
9.2
11.5
12.1
13.1
12.5
10.7
9.6
6.9
6.2
5.5
7.3
6.2
9.3
11.4
13
13.5
12.8
12.5
11.8
9.8
8.1
7.7
8.1
9.9
10.8
11.5
12
12.1
11.2
11.4
10.6
9.1
8.4
6.5
6.8
7.4
9.8
11.5
12.2
13.2
13.1
12.8
10.5
9.9
7.4
5.8
8.1
8.1
10.3
12.8
13.1
14
13.4
13.4
12.2
10.9
8.4
8.1
8.6
5.9
9
11
12.8
11.6
12.8
11.2
10
8.4
5.4
5.9
5.5
7.1
7.6
10.8
13.3
13.3
13.2
12
9.9
10.1
7.9
7.7
7.9
10.7
10.7
11.1
12.7
13.7
13.6
11.8
10.3
10.8
8.6
6.5
7.2
8.6
10
11.1
12.1
12
12.5
10.5
9.8
7.2
6.8
5
6.2
8
9.8
11.4
11.6
12.4
12.8
12.1
10.6
8.7
5.9
7.7
5.6
7.3
8.1
11.2
12.9
13
12.4
11.7
10.2
8.4
6.9
5.6
7.6
5.8
9.7
10.5
11.6
12.1
11.9
11.2
9.6
8.3
6.7
4.4
5
6.8
8.2
11.1
11.1
11.8
11.8
10.6
10.6
7.1
5.7
5.5
5.6
7.8
8.6
11.8
14
13.5
13.4
12.1
12
9.9
7.6
7.6
9
8.1
11.7
12.4
12.4
12
13.3
11.2
11
8.8
8.6
6
7
6.9
9.6
12.4
13.3
13.9
13
13.3
11.9
10.1
8.1
8.5
8.5
7.5
10.3
11.1
13.4
14.4
14.7
13.4
13.4
10.7
8.6
8.6
7.7
10.6
11.3
11.7
11.7
12
12.6
10.5
9.9
8.5
5.4
5.2
5.9
7.6
9.8
9.9
10.4
11.2
12.3
10.8
9
7.7
4.2
6.1
7.3
5.8
8.5
10.5
11.1
11
10.9
10.4
9.7
7.4
5.1
5.5
5.4
8.9
9
10.7
12.4
14
13.5
14.1
11.2
9.2
8
7.2
8.8
8.5
9.4
10.9
12.9
13.2
13.7
12.3
11.2
9.8
8.1
5.1
6.9
8.9
8.9
10.8
10.2
11.2
12
11
10.2
8.4
5.5
4.9
6.5
6.7
10
10
10.6
12.1
13.1
12
10.4
8.9
6.2
5.5
5.1
6.8
9.4
10.6
11.6
12.6
12.9
11.5
10.6
8.7
6.2
5.1
6.5
6.4
8.1
10.2
11.6
13.9
14.6
12.4
11.4
9.5
7
7.4
6.8
7.3
9.4
10.5
12.3
13.2
12.8
12
9.5
8
5.8
5.4
3.9
5.2
7.9
10.5
12.1
13.9
12.8
12.8
11.6
10.3
8.3
6.5
8.5
9.4
10.2
11.1
12.8
12.9
12.9
11.4
9.8
9.5
6.5
5.1
6.9
6.8
8.6
10.7
11.8
12.4
13.3
12.4
11.2
9.5
7.1
8.3
5.8
6.5
9
11.9
12.8
12.7
13.2
11.7
9.3
9.6
6.3
3.1
4.3
7.4
9.5
11.9
13.4
13.7
13.2
12.5
10.8
8
6.3
4.8
6.6
8.2
10
12
12.9
13.5
13.6
13.2
11.7
10.8
7.9
6.3
8.3
8.6
9.4
11.4
12.7
13.2
12.5
11.2
11.4
8.9
6.8
5.3
7.4
7.9
10.2
11
12.5
13.5
13.5
11.7
10.2
9
6.4
6.8
5.5
6.7
9.5
11.2
12.5
13
13.3
11.7
9.8
8.1
6.4
5.9
7.3
7
8.8
11.4
11.7
12.5
13.6
12.2
10.9
8.6
7.4
5.4
7.4
6
9.4
12
12.8
12.7
13.5
10.8
9.7
9.2
8.1
6.7
6.9
7.6
9.1
10.1
12.6
12.5
12.1
11.6
10.7
9.4
6.8
5.2
7.8
6
9.2
12
12.2
13.4
12.6
12.5
10.9
8.3
6.5
5.2
5.6
8
9
9.8
11.4
11.8
11.7
11.7
10.7
7.8
6.8
4.8
5.9
6.5
9.1
11.2
12.4
12.8
11.6
13.3
11.6
9.2
9.2
5.7
6.5
8.7
10.7
12.2
14
14.3
14.1
14.1
13.8
9.6
9.9
7.8
9.7
8.7
10.6
11.2
13.7
15.4
14.5
12.7
11.9
9.2
8.8
8.5
6.3
8.6
10.3
9.8
11.8
13.2
12.1
11.1
9.5
8.3
6.7
6.3
4.9
7.4
8.8
10.8
13.1
12.6
12
11.1
9.7
8.4
7.7
7.2
6.7
7.6
10.2
11.6
13.1
14
13.5
12.4
11.3
9
6.3
6.5
6.4
5.8
10.3
11.3
11.8
13.4
12.2
11.9
11.1
9.3
7.2
6.3
5.5
8.6
10.4
11.6
13.2
13.8
13.4
12.7
11.8
9.2
7.3
7.5
6.3
7
9.6
12.4
12.6
13.2
11.6
11.5
10.6
8.2
6.7
7.3
6.5
7.6
9
10.8
12.7
12.3
12.2
12.2
10.4
7.6
7.7
7.3
5.6
6.2
10.1
11.1
13.5
13
13.4
11.8
9.8
9
5.2
4.7
4.3
6.5
7.7
9.9
10.7
12.1
12
11.7
9.5
6.5
4.4
5.3
5.1
7
9.4
11.9
11.2
13.3
13.2
12.5
11.4
9.5
8.9
6.7
7.1
8.3
10.3
10.3
12.5
13
12.6
12.1
9.9
7.7
8.4
6.9
7.3
8
8.9
13.1
12.5
13.9
13
13.2
10.8
9.4
8.1
4.9
7.3
7.7
7.7
10.1
12.3
12.4
11.8
11.9
10.7
9.1
6.5
8.3
3.7
6.7
8.9
9.4
10.9
11.7
11.4
10.9
9.3
7.6
7.6
4.8
4.7
6.9
8.3
9.1
11.3
11.2
11.5
11.4
9.7
8.7
5.6
6.5
6.4
7.8
9.5
12.3
12.5
12.9
13.3
13.1
11.5
9.8
7.7
8.5
7.1
8.1
8.9
10.9
11.6
12.4
11.6
11.5
9.6
9.1
8.3
6.1
8.7
6.9
8.9
10.4
12.8
13.5
13.1
11.9
10.5
7.7
6.1
6.5
6.7
7.1
8.5
10
12.5
12.5
12.5
10.5
10.7
8.7
7.2
7.2
6.4
9.6
9.2
11.1
12.8
13.1
13.2
12.1
10.4
9.2
6.7
5.1
7.4
8.4
9.8
10.1
11.5
12.3
13.3
11.1
9.7
8.1
7.3
5.9
8
6.7
8.5
10.3
13.3
13.5
12.4
12.7
12.4
10.3
9
7.3
7.1
7
9.1
10.5
11.8
12
12.1
10.4
9.5
7.8
7.6
6.3
5.7
6.9
11.2
11.2
14
15.5
13.7
13.3
12.4
10.4
6.6
7.5
6.7
8.6
9.9
12.3
13.3
12.9
12.6
12.1
11.3
8.9
7.6
5
5.6
7.2
10.7
11
12.5
12.8
12.8
12.7
10.8
8.9
7.8
4.1
5.1
8.2
9.7
9.5
12.2
12.7
12.7
12.2
11
9.8
7.3
5.8
6.3
8.3
10.9
11
12.7
13.5
13.4
11.8
11.5
9.1
6.9
8.2
7.2
7.2
10
10.6
11.8
13.8
12
10.1
8.7
7.5
5.2
5.8
4.5
6
8
10.4
13
12.5
11.7
10.8
9.5
8.3
5.8
5.8
5.1
6.7
10.6
13.7
12.8
13.8
13.8
13.7
12.6
9.8
9.6
7.3
8.3
7
9
10.8
11
12.4
11.5
11.4
10
5.7
6.6
4
4.4
5.5
8.8
11
12.4
12.6
12.1
11
9.6
7.7
6.1
6.4
6.9
6.6
7.8
10.4
11.4
11.7
11.3
10.4
8.9
8
5.5
5.1
5.4
5.6
9.9
12
12.6
14
14.1
12.9
9.9
7.8
6.5
5.9
5.6
8.1
9.3
11.3
13.5
13.6
13.6
12.9
12.3
10
8.1
8.2
8.9
9.5
10.1
9.3
11.1
11.3
11.9
11.6
10.7
9.1
7.4
6
6.9
7.9
9.7
11.2
12.6
11.1
13.3
11.7
11
9.1
8.5
5.9
6.3
7.2
9.7
11.3
12.5
13.2
13.4
12.7
10.7
9.1
7.3
5.1
6.2
9.9
9.9
10.5
11.5
11.8
12.4
11.5
11.1
8.4
7.5
6.3
7
7.5
10.1
11.9
13.9
14.5
14.7
14
12.5
11.1
9.3
9.8
10.3
10.1
10.1
11.7
13.3
14.4
14.1
12.1
10.5
9.7
8.5
7.1
5.3
8.1
10.1
11.1
13.2
13.2
12.2
11.8
11.3
9.3
5.1
7.5
5.4
6.1
7.5
9.4
12.6
13.6
12.4
11.5
10.7
8.4
7.6
4.7
6.9
8.4
9.3
11.6
11
12.8
12
12.2
10.9
9.3
9.7
7.1
7.4
10.7
11.5
12.6
13.1
14.7
14.3
13.5
11.2
8.9
7.8
7.8
6.7
6.8
10.1
10.8
13.9
12.8
12.5
10.6
9.1
7.4
6.5
5.4
6.8
7.3
7.6
10.1
12.8
12.1
13.3
11.7
9.9
8.7
8.9
6.9
10
8.3
9.7
10.3
12.4
12.8
13.5
13.3
10.9
9.1
7.7
6.3
6.5
9.5
9.9
12.6
13.3
13.4
14
13.3
11.1
10.1
8.5
10.1
7.7
10.5
11
11.1
12.5
14.9
12.8
11.2
11.2
9.5
7.3
6.8
6.4
10.1
11.4
12.4
13.9
13.5
15.1
13.4
12
9
7
6.7
6.5
9.4
10.8
12
12.9
14.1
14.9
13.5
11.9
9.8
9.3
7
7.8
7.2
9.6
11.6
13
12.7
13.2
12
10.2
8.8
7.5
5.7
6.2
7.4
9
12.2
12.4
12.5
12.4
10.3
9.7
8.4
5.6
7.3
4.8
8.6
11.9
11.9
14.7
14.3
15.1
14.7
13.4
11.4
8.6
7.8
10.2
10
11.1
11.5
12.1
12.6
12.7

``` 

```python 
from typing import List, Tuple

def find_two_smallest(L: List[float]) -> Tuple[int, int]:
    """Return a tuple of the indices of the two smallest values in list L.

    >>> items = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    >>> find_two_smallest(items)
    (6, 7)
    >>> items == [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    True
    """

    # Sort a copy of L
    # Get the two smallest numbers
    # Find their indices in the original list L
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Get a sorted copy of the list so that the two smallest items are at the
    # front
    temp_list = sorted(L)
    smallest = temp_list[0]
    next_smallest = temp_list[1]

    # Find their indices in the original list L
    # Return the two indices

``` 

```python 
from typing import List, Tuple

def find_two_smallest(L: List[float]) -> Tuple[int, int]:
    """Return a tuple of the indices of the two smallest values in list L.

    >>> items = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    >>> find_two_smallest(items)
    (6, 7)
    >>> items == [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    True
    """

    # Get a sorted copy of the list so that the two smallest items are at the
    # front
    temp_list = sorted(L)
    smallest = temp_list[0]
    next_smallest = temp_list[1]

    # Find the indices in the original list L
    min1 = L.index(smallest)
    min2 = L.index(next_smallest)

    return (min1, min2)

``` 

```python 
import time

t1 = time.perf_counter()

# Code to time goes here

t2 = time.perf_counter()
print('The code took {:.2f}ms'.format((t2 - t1) * 1000.))

``` 

```python 
import time
import find_remove_find5
import sort_then_find3
import walk_through7

from typing import Callable, List, Any

def time_find_two_smallest(find_func: Callable[[List[float]], Any],
                           lst: List[float]) -> float:
    """Return how many seconds find_func(lst) took to execute.
    """

    t1 = time.perf_counter()
    find_func(lst)
    t2 = time.perf_counter()
    return (t2 - t1) * 1000.0

if __name__ == '__main__':
    # Gather the sea level pressures
    sea_levels = []
    sea_levels_file = open('sea_levels.txt', 'r')
    for line in sea_levels_file:
        sea_levels.append(float(line))
    sea_levels_file.close()

    # Time each of the approaches
    find_remove_find_time = time_find_two_smallest(
        find_remove_find5.find_two_smallest, sea_levels)

    sort_get_minimums_time = time_find_two_smallest(
        sort_then_find3.find_two_smallest, sea_levels)

    walk_through_time = time_find_two_smallest(
        walk_through7.find_two_smallest, sea_levels)

    print('"Find, remove, find" took {:.2f}ms.'.format(find_remove_find_time))
    print('"Sort, get minimums" took {:.2f}ms.'.format(
        sort_get_minimums_time))
    print('"Walk through the list" took {:.2f}ms.'.format(walk_through_time))

``` 

```python 
from typing import List, Tuple

def find_two_smallest(L: List[float]) -> Tuple[int, int]:
    """Return a tuple of the indices of the two smallest values in list L.

    >>> items = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    >>> find_two_smallest(items)
    (6, 7)
    >>> items == [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    True
    """

    # Examine each value in the list in order
    # Keep track of the indices of the two smallest values found so far
    # Update the indices when a new smaller value is found
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Keep track of the indices of the two smallest values found so far
    # Examine each value in the list in order
    #     Update the indices when a new smaller value is found
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Set min1 and min2 to the indices of the smallest and next-smallest
    # values at the beginning of L
    # Examine each value in the list in order
    #     Update the indices when a new smaller value is found
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Set min1 and min2 to the indices of the smallest and next-smallest
    # Values at the beginning of L
    if L[0] < L[1]:
        min1, min2 = 0, 1
    else:
        min1, min2 = 1, 0

    # Examine each value in the list in order
    #     Update the indices when a new smaller value is found
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """

    # Set min1 and min2 to the indices of the smallest and next-smallest
    # values at the beginning of L
    if L[0] < L[1]:
        min1, min2 = 0, 1
    else:
        min1, min2 = 1, 0

    # Examine each value in the list in order
    for i in range(2, len(values)):
    #     Update min1 and/or min2 when a new smaller value is found
    # Return the two indices

``` 

```python 
def find_two_smallest(L):
    """ (see above) """
	
    # Set min1 and min2 to the indices of the smallest and next-smallest
    # values at the beginning of L
    if L[0] < L[1]:
        min1, min2 = 0, 1
    else:
        min1, min2 = 1, 0

    # Examine each value in the list in order
    for i in range(2, len(L)):
    #
    #     L[i] is smaller than both min1 and min2, in between, or
    #     larger than both:
    #     If L[i] is smaller than min1 and min2, update them both
    #     If L[i] is in between, update min2
    #     If L[i] is larger than both min1 and min2, skip it
	
    return (min1, min2)

``` 

```python 
from typing import List, Tuple

def find_two_smallest(L: List[float]) -> Tuple[int, int]:
    """Return a tuple of the indices of the two smallest values in list L.

    >>> items = [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    >>> find_two_smallest(items)
    (6, 7)
    >>> items == [809, 834, 477, 478, 307, 122, 96, 102, 324, 476]
    True
    """

    # Set min1 and min2 to the indices of the smallest and next-smallest
    # values at the beginning of L
    if L[0] < L[1]:
        min1, min2 = 0, 1
    else:
        min1, min2 = 1, 0

    # Examine each value in the list in order
    for i in range(2, len(L)):
        # L[i] is smaller than both min1 and min2, in between, or
        # larger than both

        # New smallest?
        if L[i] < L[min1]:
            min2 = min1
            min1 = i

        # New second smallest?
        elif L[i] < L[min2]:
            min2 = i

    return (min1, min2)

``` 
