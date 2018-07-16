# Review of GE2324

* [Introduction](#1)
* [Network Analysis on Data](#2)
* [Data Visualization and Tools](#3)
* [Clustering Analysis](#4)
* [Data Correlation](#5)
* [Association and Frequent Item Analysis](#6)
* [Finding Similar Items](#7)

<h2 id = "1">Lec1 Introduction</h2> 

### 1. Big data

> Volume: Data at rest (TB-EB of existing data to process)
> Velocity: Data in Motion 

> Variaety: Data in many forms

> Veracity: Data in Doubt

*Big data is not about the size of the data, it is about the value within the data*

#### Hobbysit

> Byte : one grain of rice

> Kilobyte : cup of rice
> 
#### Desktop

> Megabyte : 8 bags of rice

> Gigabyte : 3 Semi trucks
> 
#### Internet

> Terabyte : 2 Container Ships

> Petabyte : Blankets Manhattan

#### Big Data

> Exabyte : Blankets west coast states

> Zettabyte : Fills the Pacific Ocean

### 2. The model of generating/consuming data has changed.

> old : Few companies are generating data.

> new: all of us are generationg data and all of us consuming data

### 3. Big data is not big

> big data -> smart data

### 4. Data Basics

- Data Definition

> Data are raw facts and
figures that on their own
have no meaning

> So Raw Data -> Context -> Information

> Information = Data + (Context + Meaning)(get by processing)

- Data Representation

> represented in binary

> change 1877 in dicimal to binary

	1877 %2 = 938 Remainder 1
	938 %2 = 469 Remainder 0
	469 %2 = 234 Remainder 1
	234 %2 = 117 Remainder 0
	117 %2 = 58 Remainder 1
	58 %2 = 29 Remainder 0
	29 %2 = 14 Remainder 1
	14 %2 = 7 Remainder 0
	7 %2 = 3 Remainder 1
	3 %2 = 1 Remainder 1
	1 %2 = 0 Remainder 1

>11101010101

- Data Transmission

> Newwork Transmission Model

> Text->digital->analog->digital->Text

> Data->Packet->Bit->Channel<-Bit->Packet->Data

- Data Storage

> Storage, also known as **mass media** or **auxiliary storage**, refers
to the various media on which a computer system can store
data.

> Storage devices hold programs and data in units called files.

> Memory is a temporary workplace where the computer transfers the contents of a file while it is being used.

<h2 id = "2">Network Analysis</h2> 

## 1. What is a Network?

> Any system of interconnected linear features

>Networks are sets of nodes connected by edges

>Networks == Graph

## 2. Network Components

> Actors: Nodes, Vertices Points
>
> Relations: Edges, Arcs, Lines, Ties

## 3. Division

> > Directed Network: single direction edges exist

> > Undirected Network: can go through it in either way no different
> 
>-----------------
>
> > Weighted: have magnitude
> 
> > Uweighted: don't have magnitude

### 4. properties

#### (1) Degree 

* number of connecting edges

>**indegree**:
how many directed edges (arcs) are incident on a node

> **outdegree**:
how many directed edges (arcs) originate at a node

> **degree**: (in or out)
number of edges on a node

> **Degree sequence**: An ordered list of the degree of each node (from large to small)
> e.g.
	
	in: [2,2,2,1,1,1,1,0]
	distribution :[(2,3)(1,4)(0,1)]
	out: [2,2,2,1,1,1,1,0]
	distribution :[(2,3)(1,4)(0,1)]
	degree: [4,3,3,3,3,2,1,1]
	distribution :[(4,1)(3,4)(2,1)(1,2)]

**!!!** When calculating degree of directed graph, notice the two arrows

#### (2) **Connected Components** 
>  **Strongly connected components**: Each node within the component can be reached from each other node in the component by following links (正反连接)

> **Weakly connected components**: every node can be reached from every other node by following links in either direction （单项链接 包括单个元素）

>In undirected networks, one simply talks about “connected components"

#### (3) path

> path != Cycle  (loop is a cycle which connects a vertex to itself)
> > In directed graph, a loop add 1 to both in-degree and out-degree
> 
> > In undirected graph, a loop add 2 to degree

#### (4) centralization

1. degree centrality(dgree) & normalized degree centrality(degree/n-1) & Degree Centrailization(sum[delta(dmax-di)] / [(n-1)*(n-2)]
2. Betweeness
3. closeness

#### (5)Comunity

1. cliques
	* all members know each other
	> maximum clique: largest possible size
	> 
	> maximal clique: a clique cannot be extended by including one more adjacent vertex
	
2.	(1) n-cliques
	
	* two actors in a subnet have a shortest path length at n (n does not have to be part of the subnet i.e. not have to be diameter)
	
	(2) n-class

	* two actors in a subnet have a shortest path length at n (n has to be part of the subnet i.e. has to be diameter)

3. k-cores
	* actors in subnet knows at least k others in the subnet
	
4. p-cores
	* def1: p = k/#actors in subnet
	* def2: p = k/#of all neibours of actor
	
[***algorithm to find n-clique(& why we don't use n-club)***](https://canvas.cityu.edu.hk/courses/23075/files/folder/(2018%20Summer)%20Lectures?preview=3307616)

#### (6) cohesion in directed & weighted networks

> If propotion of double linked ties iin graph is high "social cohesion is high"(#double linked tie*2/# of ties in the graph)

<h2 id = "3"></h2> 

<h2 id = "4"></h2> 

<h2 id = "5"></h2> 

<h2 id = "6"></h2> 

<h2 id = "7"></h2> 