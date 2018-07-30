

# Algorithm in coursera

[week 3](#3)

[week4](#4)



<h2 id = "3">Week 3 </h2>

### merge sort and quick sort

---------------------------------------
#### Interview questions 
1. Merging with smaller auxiliary array. Suppose that the subarray \mathtt{a[0]}a[0] to \mathtt{a[n-1]}a[n−1] is sorted and the subarray \mathtt{a[n]}a[n] to \mathtt{a[2*n-1]}a[2∗n−1] is sorted. How can you merge the two subarrays so that \mathtt{a[0]}a[0] to \mathtt{a[2*n-1]}a[2∗n−1] is sorted using an auxiliary array of length nn (instead of 2n2n)?

		copy only the left half into the auxiliary array
2. Shuffling a linked list

		design a linear-time subroutine that can take two uniformly shuffled linked lists of sizes n1 and n2 and combined them into a uniformly shuffled linked lists of size n1 + n2

-------------------------------------
#### Assignment3: Patter Recognition

> Computer vision: 
> Computer vision involves analyzing patterns in visual images and reconstructing the real-world objects that produced them. The process is often broken up into two phases: feature detection and pattern recognition. Feature detection involves selecting important features of the image; pattern recognition involves discovering patterns in the features. We will investigate a particularly clean pattern recognition problem involving points and line segments. This kind of pattern recognition arises in many other applications such as statistical data analysis.

[The question](http://coursera.cs.princeton.edu/algs4/assignments/collinear.html)

* How to find the maximum line(nunmber of points on a line >= 5 ) in Fast program?

	> Only add the linesegment when the original point is less than other points

	---------------------
#### The code

* [Point](https://github.com/dehezhang2/algorithm/blob/master/Sort/Patter%20Recognition/Point.java)

* [Brute](https://github.com/dehezhang2/algorithm/blob/master/Sort/Patter%20Recognition/BruteCollinearPoints.java)

* [Fast](https://github.com/dehezhang2/algorithm/blob/master/Sort/Patter%20Recognition/FastCollinearPoints.java)

----------------------------------------------
<h2 id = "3">Week 3 </h2>

### Quick sort

* Basic plan

  * recursion before the sort (merge is recursion after the sort) 
  
  * partition (put an entry to a right place) 

  * sort piece of front of the entry and tail of the entry recursively

* Step (choose the first one of the array as the entry)
	
	* i from left+1 to right, j from right to left + 1
	* until arr[i]>arr[left] && arr[j]<arr[left]
	* exchange arr[i] & arr[j] 
	* repeat 1-3 until j < i


	for(int i = left + 1, j = right; i < = j; ){
	
		if(arr[i] <= arr[left])
			i++	;	
		if(arr[j] > arr[left])
			j-- ;
		if(arr[i] > arr[left]&&arr[j]<=arr[left]){
			swap(arr[i],arr[j]);
		}
	}

* Notice

	* stay in the bound (test needed):
	- [] (j==left)
	- [x] (i==right)
	
	* Shuffle the array before sort: for performance(quadratic case)
	
	* Equal keys: when duplicates are present, it is better to stop on keys equals to the partitioning item's key

* Properties

	* in-place: 
	
		> Partition: constant extra place Depth of recursion
		>
		> Depth of recursion: logarithmic extra space

	* not stable
	
* improvements

	* Insertion of small arrays(10 items)

	* median of sample: choose the median as a entry(swap median and left)

### Selection

* Goal: Given an array of N items, find the k-th largest

* Use theory as a guide:

	* Upper bound: NlogN
	* Upper bound for k = 1 ,2 ,3.:N How?
	> go through the array
	
	* Lower bound : N Why?

* Quick selection 
	> Partition array until j == the k order you want (again shuffle before the partition)

* proposition: Linear time on average

### Duplicate Keys

* large array but small # of key values

* Mergesort : Always between 1/2*NlgN and NlgN compares

* QuickSort: quadratic times unless patition stops at equal keys

  * recommend: stops scans on items equal to the partitioning item

* 3-way partitioning
  * Entries between lt and gt: equal

  ```
  v=a[lo];lt=lo;gt=hi;i=lo+1;
  
  (a[i]<v) swap(a[lt++],a[i++]]);
  
  (a[i]>v) swap(a[gt--],a[i]]);
  
  (a[i]==v) i++;
  
  until i>= gt
  ```

  

### System sort

* java system sorts: Array.sort();

  * different methods for each primitive type

  * a method for data types that implements Comparable

  * a method uses COmparator

  * Uses tuned quicksort fpr primitive types, tuned mergesort for objects(stable, space is not that important)

  * import java.util.arrays

* Tukey's ninther

  > small arrays: middle entry
  >
  > medium arrays: median of 3(3 ways partitioning)
  > 
  > large arrays: Tukey's ninther

  * pick 9 items out of the array

  * take the median of the mediums as a ninther

  ```
  9 samples: RAM GXK BJE
  
  medians: MKE
  
  ninther: K
  ```

  

* Interview questions: 

* Decimal dominants. Given an array with nn keys, design an algorithm to find all values that occur more than n/10n/10 times. The expected running time of your algorithm should be linear.

  ```
  Hint: determine the (n/10)th largest key using quickselect and check if it occurs more than n/10 times.
  
  Alternate solution hint: use 9 counters.
  ```

  

* Selection in sorted array: 2 arrays a[] b[], size n1, n2 find kth largest key. log(n1+n2) algorithm

  ```
  Approach A: Compute the median in a[] and the median in b[]. Recur in a subproblem of roughly half the size.
  
  Approach B: Design a constant-time algorithm to determine whether a[i] is the kth largest key. Use this subroutine and binary search.
  ```

------

<h2 id = "4">Week 4</h2>

### Priority Queues

------

### APIs and Elemnentary Implementations

- Collections: Insert and delete items

  > Stack: Remove the items most recently added
  >
  > Queue: Remove the items least recently added
  >
  > Randomized Queue: Remove a random item
  >
  > Priority queue: Remove the largest/smallest item

- Find largest M items in a stream of N items(large M frauds in N transactions)

- ```java
  MinPQ<Transaction> pq = new MinPQ<Transaction>();
  while(StdIn.hasNextLine()){
      String line = StdIn.readLine();
      Transaction item = new Transaction(Line);
      pq.insert(item);
      //delete items not topM
      if(pq.size()>M)
      	pq.delMin();
  }
  ```

  | implementation |  time   | space |
  | :------------: | :-----: | :---: |
  |      sort      | N logN  |   N   |
  | elementary PQ  |   M N   |   M   |
  |  binary heap   | N log M |   M   |
  | best in theory |    N    |   M   |

- unordered array implementation

  ```java
  public class UnorderedMaxPQ<Key extends Comparable<Key>>{//key is comparable
      private Key[] pq;
      private int N;
      public UnorderedMaxPQ (int capacity){
          pq = (Key[]) new Comparable[capacity];
      }
      public boolean isEmpty(){
          return N==0;
      }
      public void insert(Key x){
          pq[N++] = x;
      }
      public Key delMax(){
          int max = 0;
          for(int i=1;i<n;i++)
              if(less(max,i)) max = i;
          //put to the end return and reduce the size
          swap(max,N-1);
          return pq[--N];
      }
      public boolean less(int x,int y){
          return pq[x].toCompare(pq[y])<0;
      }
      public void swap(int x,int y){
          Key temp = pq[x];
          pq[x] = pq[y];
          pq[y] = temp;
      }
  }
  ```



| impelementation  | insert | del max | max  |
| ---------------- | ------ | ------- | ---- |
| unoredered array | 1      | N       | N    |
| ordered array    | N      | 1       | 1    |
| goal             | logN   | logN    | logN |



* Use binary search to insert a key into ordered array, but when shifting we still need linearly array accesses.



-----------------

### Binary Heaps

* Complete binary tree

  * Binary tree: empty or node with links to left and right binary trees (only two branches for each nodes)
  * Complete tree: perfectly balanced, except for bottom level (except the bottom level, all of the level must be full)
  * Property: Height of complete tree with N nodes is [lg N]
  * Pf: Height only increases when N is a power of 2

* Binary heap: array representation of a heap-ordered complete binary tree

  * keys in nodes 
  * parent's key no smaller than children's keys

* Array representation

  * Indices start at 1(the largest key)
  * Takes nodes in level order
  * No explicit links needed
  * Parent of node at k: k/2
  * Children of node at k: 2k and 2k + 1

* Scenario: Child's key becomes larger key than its parent's key

  * exchange key in child with key in parent
  * repeat until heap order restored

  ```java
  private void swim(int k){
      while(k>1 && less(k/2,k)){
          swap(k,k/2);
          k=k/2;
      }
  }
  // logN+1 compares
  public void insert(Key x){
      pq[++N]=x;
      swim(N);
  }
  ```

  

* Scenario: parent is smaller than its child

  * exchange key with larger child

  ```java
  private void sink(int k){
      while(2*k<=N){
          int j = 2*k;
          // find max child
          if(j<N && less(j,j+1)) j++;
          if(!less(k,j)) break;
          swap(k.j);
          //check next
          k = j;
      }
  }
  public Key delMax(){
      Key max = pq[1];
      swap(1,N--);
      sink(1);
      pq[N+1] = null;
      return max;
  }
  ```

  



------------------

### Heapsort

### Event-Driven Simulation

### 8 Puzzle

