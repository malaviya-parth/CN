## Distance Vector Routing
- It is based upon Bellman ford Algorithm.
- It was original ARPANET routing algorithm.
- It was also used in internet under the name RIP.
- Initially every router has idea about total number of routers in the Network.
- Weight on edge can be distance, No. of hops, delay, etc.
- Each router maintains a table in which the fields are "To" "Cost" & "Next".
- The number of entries is equal to the number of routers in the network.
- Since, It is a type of distributive algorithm so learning is always done from neighbours
- Periodically each router share cost column [Distance Vector] of its table with all it's neighbours only.
- Entire table is not shared rather cost column is shared.
- ```
    D --- C
    | \   |
    |   \ |
    A --- B
    ```
- Cost D-C:11, C-B:3, A-B:2, A-D:1, B-D:7
- Routing Tables:

D
| To | Cost | Next |
| -- | ---- | ---- |
| A  |  1   |   A  |
| B  |  7   |   B  |
| C  |  11  |   C  |
| D  |  0   |   D  |
C
| To | Cost | Next |
| -- | ---- | ---- |
| A  |  inf |   -  |
| B  |  3   |   B  |
| C  |  0   |   C  |
| D  |  11  |   D  |
A
| To | Cost | Next |
| -- | ---- | ---- |
| A  |  0   |   A  |
| B  |  2   |   B  |
| C  |  inf |   -  |
| D  |  1   |   D  |
B
| To | Cost | Next |
| -- | ---- | ---- |
| A  |  2   |   A  |
| B  |  0   |   B  |
| C  |  3   |   C  |
| D  |  7   |   D  |

- This table is filled with help of packets called as "Hello packets".
### After first table exchange with neightbours
D gets new vales:  
C: inf,3,0,11 & A: 0,2,inf,1  
C: inf,13,11,22 & A: 1,3,inf,2  
D's updated table:

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  1   |   A  |
| B  |  3   |   A  |
| C  |  11  |   C  |
| D  |  0   |   D  |

C's updated table after getting values from D & B  

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  5   |   B  |
| B  |  3   |   B  |
| C  |  0   |   C  |
| D  |  10  |   B  |

B's updated Table after getiing values from C, A & D.   
C: inf,3,0,11 D: 1,7,11,0 A: 0,2,inf,1   
C: inf,3,3,14, D: 8,7,18,7 A: 2,2,inf,3

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  2   |   A  |
| B  |  0   |   B  |
| C  |  3   |   C  |
| D  |  3   |   A  |

A's updated Table after getting values from D & B.

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  0   |   A  |
| B  |  2   |   B  |
| C  |  5   |   B  |
| D  |  1   |   D  |

### After Second Table exchange with neighbours
- This time the updated cost vectors will be changed

D gets value from A & C  
A: 0,2,5,1 C: 5,3,0,10  
A: 1,3,6,1 C: 16,14,11,10  
D's updated table

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  1   |   A  |
| B  |  3   |   A  |
| C  |  6   |   A  |
| D  |  0   |   D  |

At C  
D: 1,3,11,0 B: 2,0,3,3  
D: 12,14,11,11 B: 5,3,3,6 

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  5   |   B  |
| B  |  3   |   B  |
| C  |  0   |   C  |
| D  |  6   |   B  |

B's Table 

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  2   |   A  |
| B  |  0   |   B  |
| C  |  3   |   C  |
| D  |  3   |   A  |

A's Table

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  0   |   A  |
| B  |  2   |   B  |
| C  |  5   |   B  |
| D  |  1   |   D  |

### After third exchange with neighbours

D's Table

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  1   |   A  |
| B  |  3   |   A  |
| C  |  6   |   A  |
| D  |  0   |   D  |

C's Table

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  5   |   B  |
| B  |  3   |   B  |
| C  |  0   |   C  |
| D  |  6   |   B  |

B's Table

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  2   |   A  |
| B  |  0   |   B  |
| C  |  3   |   C  |
| D  |  3   |   A  |

A's Table

| To | Cost | Next |
| -- | ---- | ---- |
| A  |  0   |   A  |
| B  |  2   |   B  |
| C  |  5   |   B  |
| D  |  1   |   D  |

- All these table are same as previous exchange tables so we can say that no more exchanges are needed.

## Question
Which edge will be never used?

### Solution
- From D there are routes only to A, so no usage of DC and DB edge.
- Same from B no path to D, from C no path to D.

## Note
> If packet is not sent by D via DB then B will also not send the packet to D via BD. The links here are symmetric or can say two ways that's why if one side doesn't send via that link, other side will use the same other path used by first side.

## Important Points
- If we have 'n' routers in the Network then n-1 steps or rounds are needed by every router to crack their table.
- In 1st step, 1 edge is involved.
- In 2nd step, 2 atmost edges are involved.
- In (n-1)th step, atmost (n-1)edges are involved.
- Since, DVR is a kind of Adaptive [Dynamic] Routing algorithm so it won't stop even after (n-1) steps rather routers keep on exchanging tables periodically because some router may fail pr link may go down, etc.