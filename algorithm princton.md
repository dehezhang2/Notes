

# Algorithm in coursera

[week 3](#3)

[week4](#4)

[week5](#5)

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


```java
for(int i = left + 1, j = right; i < = j; ){

	if(arr[i] <= arr[left])
		i++	;	
	if(arr[j] > arr[left])
		j-- ;
	if(arr[i] > arr[left]&&arr[j]<=arr[left]){
		swap(arr[i],arr[j]);
	}
}
```

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

  ```java
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

### 1. Priority Queues

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
          if(j<N && less(j,j+1)) j++;	//here are N entries, start from 1 so N is the last 
          if(!less(k,j)) break;
          swap(k.j);
          //check next
          k = j;
      }
  }
  public Key delMax(){
      Key max = pq[1];
      swap(1,N--);
      pq[N+1] = null;
      sink(1);
      return max;
  }
  ```

  ```java
  public class MaxPQ<Key extends Comparable<Key>>{
      private Key[] pq;
      private int N;
      public MaxPQ(int capacity){
          pq = (Key[]) new Comparable[capacity+1];
      }
      public boolean isEmpty(){return N==0;}
      public void insert(Key key);
      public Key delMax();
      public void swim(int k);
      public void sink(int k);
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

  

* Immutability of keys

  * Assumption: client doesn't change keys while they're on the PQ

  * Best practice: use immutable keys

  * Data type: set of values and operations on those values

  * Immutable data type: Cannot change the data type value once created (String Integer Double Color Vector...)

    

  * ```java
    public final class Vector{
        private final int N;
        private final double[] data;
        public Vector(double[] data){
            this.N = data.length;
            this.data = new double[N];
            for(int i=0;i<N;i++)
                this.data[i]=data[i];
        }
    }
    ```

    

* Underflow and overflow(exception)

  * throw exception if deleting from emty
  * add no-arg constructor and use resizing array

* Minimum-oriented priority queue

  * Replace less() with greater()
  * Implement greater()

* Other operations

  * Remove an arbitrary item
  * change the priority of an item //sink() and swim()

------------------

### Heapsort

* Basic plan for in-place sort
  * Create max-heap with all N-keys
  * Repeatedly remove the maximum key
* Heap construction
  * Build max heap using bottom-up method (check all the 3-nodes heap from bottom)
* remoce maximum
  * swap(1, N--) then the largest one to the tail of the heap (array)

```java
public static void sort(Comparable[] pq){
 	int N = pq.length;
	//from the second last layer to sink make the heap in order
	for(int k = N/2; k >= 1; k--)
    	sink(arr,k,N);
	// remove the maximum, one at a time
	while(N>1){
    	swap(arr,1,N--);
    	sink(arr,1,N);
	}
}
// N*logN(<=2N compares and exchanges in heap construction,<= 2NlogN comparaes and exchanges for heapsort) In-place sorting with NlogN worst case
```

* bottom line (heapsort is not often used)
  * Inner loop longer than quicksort's
  * Makes poor use of cache memory(高速缓存)
  * not stable

-----

### Event-Driven Simulation

* Goal: simulate the motion of N moving particles that behave according to the laws of elastic collision

* Hard disc model

  * moving particles via elastic collisions with each other and walls
  * each particle is a disc(圆盘) with known position, velocity, mass and radius
  * No other forces

  ```java
  public class BouncingBalls{
      public static void main(String[] args){
  		int N = Interger.parceInt(arg[0]);
          Ball[] balls = new Ball[N];
          for(int i=0;i<N;i++)
              balls[i]=new Ball();
          while(true){
              StdDraw.clear();
              for(int i=0;i<N;i++){
                  balls[i].move(0.5);
                  balls[i].draw();
              }
              StdDraw.show(50);
          }
      }
  }
  public class Ball{
      private double rx,ry;
      private double vx,vy;
      private final double radius;
      public Ball(){/*initialize position and velocity*/}
      public void move(double dt){
          //check collision with walls
          if((rx+vx*dt<radius)||(rx+vx*dt>1.0-radius)){vx=-vx;}
          if((ry+vy*dt<radius)||(ry+vy*dt>1.0-radius)){vy=-vy;}
          rx+=(vx*dt);
          ry+=(vy*dt);  
      }
      public void draw(){
          StdDraw.filledCircle(rx,ry,radius);
      }
  }
  ```

  

* Missing : collision between each other

* Time-driven simulation

  * Discretize time in quanta of size ***dt***
  * Update the position of each particle after every ***dt*** units of time and check overlap
  * If overlap, roll back the clock to the time of the collision, update the velocities of the colliding particles, and continue the simulation
  * Drawbacks: quadratic slow 

* Even-driven (Change state only when something happened)

  * Between collisions, particles move in straight-line trajectories(弹道)
  *  Focus only on times when collisions occur
  * Maintain PQ of collision events, prioritized by time
  * Remove the min = get next collision

  > Prediction: at time ***t*** use position velocity and radius 
  >
  > Resolution: at time ***t + dt*** change the veocity 

  ```java
  public class Particle{
      private double rx,ry;
      private double vx,vy;
      private final double radius;
      private final double mass;
      private int count;
      public Particle(...){}
      public void move(double dt){}
      public void draw(){}
      //predict collision with particle or wall
     	public double timeToHit(Particle that){}
      public double timeToHitVerticalWall(){}
      public double timeToHitHorizontalWall(){}
      //resolve collision with particle or wall
     	public void bounceOff(Particle that){}
     	public void bounceOffVerticalWall(){}
      public void bounceOffHorizontalWall(){}
  }
  ```

  * Initialization

    * Fill PQ with all potential particle-wall collisions
    * Fill PQ with all potential particle-particle collisions

  * Main loop

    * delete the impending(即将到来的) event from PQ
    * If the event has been invalidated, ignore it
    * Advance all particles to time t, on a straight-line trajectory
    * Update the velocities of the colliding particles
    * Predict future particle-wall and particle-particle collisions involving the colliding particles and insert events onto PQ

    ```java
    private class Event implements Comparable<Event>{
        private double time;
        private Particle a,b;
        private int countA,countB;
        public Event(double t,Particle a,Particle b){}
        public int comparaTo(Event that){
            return this.time-that.time;
        }
        public boolean isValid(){}
    }
    public class CollisionSystem{
        private MinPQ<Event> pq;
        private double t = 0.0;
        private Particle[] particles;
        public CollisionSystem(Particle[] particles){}
        private void predict(Particle a){
            if(a == null) return;
            for(int i=0;i<N;i++){
    			double dt = a.timeToHit(particles[i]);
                pq.insert(new Event(t+dt,a,particles[i]));
            }
            pq.insert(new Event(t+a.timeToHitVerticalWall()),a,null);
            pq.insert(new Event(t+a.timeToHitHorizontalWall()),null,a);
        }
        private void redraw(){}
        public void simulate(){
            pq = new MinPQ<Event>();
            for(int i=0;i<N;i++)predict(particles[i]);
            pq.insert(new Event(0,null,null));
            while(!pq.isEmpty()){
                Event event = pq.delMin();
                if(!event.isValid())continue;
                Particle a = event.a;
                Particle b = event.b;
                for(int i=0;i<N;i++)
                    particles[i].move(event.time-t)
                t=event.time;
                if(a!=null&&b!=null)a.bounceOff(b);
                else if(a!=null&&b==null)a.bounceOffVerticalWall();
                else if(a==null&&b!=null)a.bounceOffHorizontalalWall();
                else if(a==null&&b==null)redraw();
                //predict new event
                predict(a);
                predict(b);
            }
        }
    }
    ```

    





-------------------

### Interview questions

* Dynamic median(insert and remove in logarithmic, find the median in constant )
  * two heap one is max-oriented another is min-oriented
* Taxocab numbers: find all numbers can be represneted in two forms of cubic: a^3+b^3=c^3+d^3=n
  * form the sums a^3+b^3 and sort
  * use a min-oriented priority queue with n items

### 8 Puzzle

-----------

### 2. Elementary symbol tables

---------

### Symbol tables API

(1) Key - value pair abstraction

* Insert a value with specified key
* Given a key, search for the corresponding value.

```java
public ckass ST<Key,Value>{
    ST();	//create a symbol table
    void put(Key key, Value val);	//put key-value pair into the table like arr[key] = value
    Value get(Key key);	//like int val = arr[key]
    void delete(Key key){
        put(key,null);
        size--;
    }
    boolean contains(Key key){
        return get(key)!=null;
    }
    boolean isEmpty();
    int size();
    Iterable<Key> keys();
}
```



(2) Conventions

* Values are not ```null``` 
* Method ```get()``` returns ```null``` if key not present
* Method ```put()``` overwrites old value with new value

(3) Keys and Values

* Values: Any generic type
* Keys: 
  * Assume keys are ```Comparable``` , use ```compareTo()```. 
    * more efficient implements by using the ordering of the keys to find ways around the data structure
    * support broader symbol table operations
  * Assume keys are any generic type, use ```eauals()``` to test equality
  * Assume keys are any generic type, use ```eauals()``` to test equality, use ```hashCode()``` to test scarmble(争夺) key.

* Best practices : immutable types for symbol table keys(String Integer Double java.io.File)

  

  (4) Equality test

  * Reflexive: x.equals(x) is true
  * Symmetric: x.equals(y) iff y.equals(x)
  * Transitive: if x.equals(y) and y.equals(z), then x.equals(z)
  * Non-null: x.equals(null) is false

  ```java
  public class Date implements Comparable<Date>{
  	private final int month;
      private final int day;
      private final int year;
      public boolean equals(Object y){
          if(y==this) return true;	//if the reference is the same
          if(y==null) return false;	//if y is null
          if(y.getClass()!=this.getClass())	//same class?
              return false;
          Date that = (Date) y;
          return (this.day==that.day)&&(this.month==that.month)&&(this.year==that.year);
      }
  }
  ```

(5) "Standard" recipe for user-defined types

* Optimization for reference equality (use ```getClass()```)

* Check against null

* Check two objects are of the same type and cast

* Compare each significant field

  > if field is a primitive type use ==
  >
  > If field is an object, use equals()
  >
  > if field is an array, apply to each entry use ```Arrays.equals(a,b)``` or ```Array.deepEquals(a,b)``` 

* Best practices

  * No need to use calculated fields(dependent fields)
  * Compare fields most likely to differ first
  * Make ```compareTo()``` consistent with ```equals()``` (use first one if it is a Comparable type)

  ```java
  // example of find most frequent word using Symbol table
  public class FrequencyCounter{
      public static void main(String[] args){
          int minlen = Integer.parseInt(args[0]);
          ST<String, Integer> st = new ST<String,Integer>();
          while(!StdIn.isEmpty()){
              String word = StdIn.readString();
              if(word.length()<minlen)continue;
              if(!st.contains(word))st.put(word,1);
              else st.put(word,st.get(word)+1);
          }
          String max="";
          st.put(max,0);
          for(String word:st.keys())
              if(st.get(word)>st.get(max))
                  max=word;
          StdOut.println(max+" "+st.get(max));
      }
  }
  ```

------------------

### Elementary Implementations

* Linked list

  * Data structure: linked list with key-value pairs
  * Search: Scan through all keys until find a match
  * Insert: Scan through all keys until find a match; if no add to front
  * for keys only have interface ```equals()```
  * Linearly time

* Binary Search

  * ordered array
  * for keys have interface ```compareTo()```;
  * Log search and linear insert

  ```java
  private Key[] keys;
  private Value[] vals;
  private int N;
  public Value get(Key key){
      if(isEmpty())return null;
      int i = rank(key);
      if(i<N && keys[i].compareTo(key)==0) return vals[i];
      else return null;
  }
  private int rank(Key key){
      int left = 0, right = N - 1; 
      while(left<=right){
          int mid = (left+right)/2;
          int cmp = key.compareTo(keys[mid]);
          if(cmp<0) right=mid-1;
          else if(cmp>0) left = mid + 1;
          else return mid;
      }
      return left;
  }
  public void insert(Key key,Value value){
      if(isEmpty) {
          keys[N++]=key;
          vals[N++]=value;
      }
      else if(get(key)==null){
      	int i = rank(key);
          for(int j = N-1;j>=i;j--){
              vals[j+1]=vals[j];
              keys[j+1]=keys[j];
          }
          vals[i]=value;
          keys[i]=key;
      }
      else{
          int i = rank(key);
          vals[i]=value;
      }
  }
  ```

  --------------

  ### Ordered symbol table 

  API

  ```java
  public class ST<Key extends Comparable<Key>,Value>{
      ST
      //...
      Key min();
      Key max();
      Key floor(Key key);
      Key ceiling(Key key);
      
  }
  ```

  -----------

  ### Binary Search Trees

  (1) Defination

  * Binary Heap: implicit representation of trees with an array

  * Binary search tree: explicit binary search tree in symmetric order

  * ***Symmetric*** order: each node has a key, and every node's key is:

    * **Larger** than all keys in its left subtree
    * **Smaller** than all keys in its right subtree

  * Java: A BST is a reference to a root Node

  * A Node is comprised of four fields:

    * A Key and a Value
    * A reference to the left and right subtree

    ```java
    public class BST<Key extends Comparable<key>,Value>{
        private Node root;	//root of BST
    	private class Node{
        	private Key key;
        	private Value val;
        	private Node left,right;
        	public Node(Key key,Value val) {
            	this.key = key;
            	this.val=val;
        	}
    	}
        
        /*public void put(Key key,Value val){
    		Node x = root;
            while(x!=null){
                int cmp = key.compareTo(x.key);
                if(cmp<0) x = x.left;
                else if(cmp>0) x = x.right;
                else x.val = val;
            }
            if(x==null) x = new Node(key,val);
        }*/
        
        //recursive implementation
        public void put(Key key,Value val){
            root = put(root,key,val);
        }
        private Node put(Node x,Key key,Value val){
            if(x==null) return new Node(key,val);//for the new node
            int cmp = key.compareTo(x.key);
            if(cmp<0)
                x.left = put(x.left,key,val);
            else if(cmp>0)
                x.right = put(x.right,key,val);
            else
                x.val = val;
            return x;	//every time return the processed same node
        }
        
        public Value get(Key key){
           	Node x = root;
            while(x!=null){
                int cmp = key.compareTo(x.key);
                if(cmp<0) x = x.left;
                else if(cmp>0) x = x.right;
                else return x.val;
            }
            return null;
        }
        
        public void delete(Key key){
    		
        }
        
        public Iterable<Key> iterator(){
            
        }
    }
    
    ```

  (2) mathematical analysis

  * Proposition: If N distinct keys are inserted into a BST in random order, the expected number of compares for a search/insert is ~2 $ln N$
  * Pf: 1-1 correspondence with quicksort partitioning
  * But for ordered key the time would be linear

  (3) other methods

  * Min: ```while(x!=null) x=x.left;```

  * Max: ```while(x!=null) x=x.right;```

  * Floor: largest key <= given key

    * Case1: [key equals the key at root] -> the floor of $k$ is $k$
    * Case2: [key is less than the key at root] -> The floor of k is in the left subtree
    * Case3: [key is larger than the key at root] -> The floor of k is in the right otherwise the root

    ```java
    public Key floor(Key key){
        Node x = floor(root,key);
        if(x==null) return null;
        return x.key;
    }
    private Node floor(Node x,Key key){
        if(x==null) return null;
        int cmp = key.compareTo(x.key);
        if(cmp==0) return x;
        if(cmp<0) return floor(x.left,key);
        // right otherwise the root
      	Node t = floor(x.right, key);
        if(t!=null) return t;
        else 		return x;
    }
    ```

    

  * Ceiling:  smallest key >= given key

  * ```rank()```, ```select()``` what is the rank of a given key, what is the key of the given rank

  * ```size()``` return the count at the root

  * ```java
    private class Node{
        private Key key;
        private Value val;
        private Node left,right;
        private int count;
        public Node(Key key,Value val,int cnt) {
            this.key = key;
            this.val=val;
            count = cnt;
        }
        public int size(){
            return size(root);
        }
        private int size(Node x){
            if(x==null) return 0;
            return x.count;
        }
    }
    public void put(Key key,Value val){
    	root = put(root,key,val);
    }
    private Node put(Node x,Key key,Value val){
    	if(x==null) return new Node(key,val,1);//for the new node
        int cmp = key.compareTo(x.key);
        if(cmp<0)
           x.left = put(x.left,key,val);
        else if(cmp>0)
           x.right = put(x.right,key,val);
        else
           x.val = val;
        x.count = 1 + size(x.left) + size(x.right);	//1 is the node itself
        return x;	//every time return the processed same node
    }
    public int rank(Key key){
        return rank(key,root);
    }
    private int rank(Key key,Node x){
        if(x==null) return 0;
        int cmp = key.compareTo(x.key);
        if(cmp<0) return rank(key,x.left);
        //the current node and left nodes all less than the key
        else if(cmp>0) return 1 + size(x.left) + rank(key,x.right);	
        else return size(x.left);
    }
    ```

    

  * Inorder traversal

    * Traverse left subtree
    * Enqueue key
    * Traverse right subtree

    ```java
    public Iterable<Key> keys(){
        Queue<Key> q = new Queue<Key>();
        inorder(root,q);
        return q;
    }
    private void inorder(Node x, Queue<Key> q){
        if(x==null) return;
        inorder(x.left,q);
        q.enqueue(x.key);
        inorder(x.right,q);
    }
    ```

    

