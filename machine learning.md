













# Machine Learning

[TOC]



-------------

## Week1

-------

### What is Machine Learning?

* Field of study that gives computer the ability to learn without explicity programmed

* A computer program learn from experience E with respect to some task T and some performance measure P, if its Performance of T, measured by P improves with E.

  * T: play check
  * P: probability to win
  * E: play thousands of games

* Machine learning algorithms

  * Supervised learning : teach computer how to do something
    * give the computer data (right answer) use the data to do something
    *  regression problem: fit a line to predict
    * Classification: discrete valued output(0 or 1)
  * Unsupervised learning : Data has no label (clustering algorithm)
  * Reinforcement learning
  * recommender systems

  

  ----------------------

  ### Model and Cost Function

  #### 1. Model representation

  * Some definations

    * Data set -> Training set
    * m = training set . size()
    * x's "input" variables
    * y's "output" variables
    * (x,y) -> a training example
    * (x(i),y(i)) -> ith training example

  * Process

    * training set -> Learning algorithm -> h（function as output of learning algorithms）hypothesis

    * x -> h -> y

    * $$
      h_{ \theta}(x) = {\theta}_0+{\theta}_1x
      $$

    * $ \theta $ is parameter and the function represent a line： named as **linear regression** with one variable -> **Univariate(one var) linear regression**

  -----------------

  #### 2. Method

  * Idea : choose $ {\theta}_0  {\theta}_1$ that $h_\theta(x)$ is close to y for our training examples (x,y)

  $$
  \theta_0, \theta_1 -> {{1\over{2m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 }_{min}
  $$

  ​	
  $$
  J(\theta_1,\theta_2) = {{1\over{2m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 }
  $$

  *  J is the cost function with input $ \theta $, we need find $ J_{min} $
    * Suppose $ \theta_0 $ is 0, then draw the graph of J -> a bow shipe graph
    * for two parameters we use contour plots(figures)
      * X-axis : $ \theta_0 $ Y-axis : $ \theta_1 $
      * Every circle represent same value of $ J(\theta_0, \theta_1)  $ (等高线, 3-D 图的投影)

---------------------

### Parameter Learning

----------

#### 1. Algorithm to calculate $ J_{min} $ : Gradient descent(梯度下降)

* Outline

  * Start with some $ \theta_0 , \theta_1$ (say the two parameters are both zero)
  * Keep changing $ \theta_0 , \theta_1$ to reduce$ J(\theta_0 , \theta_1) $ until end up at a minimum

  repeat until convergence {

  
  $$
  \theta_j := \theta_j - \alpha {\delta\over\delta\theta_j }J(\theta_0 , \theta_1)\  (for\ j=0\ and\ j=1)
  $$
  }

  > := assignment 
  >
  > $ \alpha $ is learning rate : size of steps down the hill
  >
  > update & \theta_0 , \theta_1 & at the same time (simultaneous update)

  ```
  temp0 = theta0 - something(theta0,theta1);
  temp1 = theta1 - something(theta0,theta1);
  // update by old value first
  theta0 = temp0;
  theta1 = temp1;
  ```

------------

#### 2. Gradient Descent Intuition

* first suppose $ \theta_0 = 0 $

  * Use $  \alpha {\delta\over\delta\theta_j }J(\theta_0 , \theta_1)  $ if delta \<(\>) 0 then go right(left) , when =0 stop
  * $\alpha$: small->slow large->fail to converge

* Used in Linear Regression
  $$
  {\delta\over\delta\theta_j }J(\theta_0 , \theta_1) = {\delta\over\delta\theta_j }{{1\over{2m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 } = {\delta\over\delta\theta_j }{{1\over{2m}}\sum_{i=1}^m(\theta_0+\theta_1x^i-y^i)^2 }
  $$

  $$
  j=0:{\delta\over\delta\theta_0 }J(\theta_0 , \theta_1)={{1\over{m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 }
  $$

  $$
  j=1:{\delta\over\delta\theta_1 }J(\theta_0 , \theta_1)={{1\over{m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 }*x^i
  $$

  * J is Convex function 

* "Batch" Gradient Descent: Batch is each step of gradient descent uses **all** the training examples

-------------

#### 3. Linear Algebra

- Matrix in Matlab/Octave 

  ```matlab
  % The ; denotes we are going back to a new row.
  A = [1, 2, 3; 4, 5, 6; 7, 8, 9; 10, 11, 12]
  
  % Initialize a vector 
  v = [1;2;3] 
  
  % Get the dimension of the matrix A where m = rows and n = columns
  [m,n] = size(A)
  
  % You could also store it this way
  dim_A = size(A)
  
  % Get the dimension of the vector v 
  dim_v = size(v)
  
  % Now let's index into the 2nd row 3rd column of matrix A
  A_23 = A(2,3)
  % Initialize matrix A and B 
  A = [1, 2, 4; 5, 3, 2]
  B = [1, 3, 4; 1, 1, 1]
  
  % Initialize constant s 
  s = 2
  
  % See how element-wise addition works
  add_AB = A + B 
  
  % See how element-wise subtraction works
  sub_AB = A - B
  
  % See how scalar multiplication works
  mult_As = A * s
  
  % Divide A by s
  div_As = A / s
  
  % What happens if we have a Matrix + scalar?
  add_As = A + s
  
  % The ; denotes we are going back to a new row.
  A = [1, 2, 3; 4, 5, 6; 7, 8, 9; 10, 11, 12]
  
  % Initialize a vector 
  v = [1;2;3] 
  
  % Get the dimension of the matrix A where m = rows and n = columns
  [m,n] = size(A)
  
  % You could also store it this way
  dim_A = size(A)
  
  % Get the dimension of the vector v 
  dim_v = size(v)
  
  % Now let's index into the 2nd row 3rd column of matrix A
  A_23 = A(2,3)
  
  B=A*v
  % Initialize a 3 by 2 matrix 
  A = [1, 2; 3, 4;5, 6]
  
  % Initialize a 2 by 1 matrix 
  B = [1; 2] 
  
  % We expect a resulting matrix of (3 by 2)*(2 by 1) = (3 by 1) 
  mult_AB = A*B
  
  % Make sure you understand why we got that result
  
  % Initialize random matrices A and B 
  A = [1,2;4,5]
  B = [1,1;0,2]
  
  % Initialize a 2 by 2 identity matrix
  I = eye(2)
  
  % The above notation is the same as I = [1,0;0,1]
  
  % What happens when we multiply I*A ? 
  IA = I*A 
  
  % How about A*I ? 
  AI = A*I 
  
  % Compute A*B 
  AB = A*B 
  
  % Is it equal to B*A? 
  BA = B*A 
  
  % Note that IA = AI but AB != BA
  
  %transpose and invert
  A_trans = A'
  A_invA = inv(A)
  ```

- for $ \vec{x}=[x_1;x_2;...;x_n] $ , we use matrix to find $\theta_0, \theta_1$
  $$
  \begin{bmatrix}1&x_1\\1&x_2\\\vdots&\vdots\\1&x_m\\\end{bmatrix}\cdot\begin{bmatrix}\theta_0\\\theta_1\end{bmatrix}=\begin{bmatrix}y_1\\y_2\\\vdots\\y_m\end{bmatrix}
  $$
  

## Week 2

--------------

### 1. Multivariate Linear Regression

------------

#### (1) Multiple Features

* Features -> {$x_1,x_2,...,x_n$} -> $y$ -> Price

* Notation:

  * $n$ = number of features
  * $x^{(i)}$ = input (features) of $i^{th}$ training example (n dimentional vector) : 第i组sample
  * $x{^{(i)}_j}$ = value of feature $j$ in $i^{th}$ training example： 第j个feature

* Hypothesis:
  $$
  h_\theta(x) = \theta_0x_0+\theta_1x_1+...+\theta_nx_n = {\theta^T}X
  $$
  For convenience of notation, define $x_0 = 1$ ($x{^{(i)}_0} = 1$)

  

  
  $$
  h_\theta(x) = \theta_0x_0+\theta_1x_1+...+\theta_nx_n = {\theta^T}X
  $$


$$
J(\theta)=J(\theta_0,\theta_1,...,\theta_n) = {{1\over{2m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 }
$$

$$
\theta_j:= \theta_j -\alpha {{1\over{m}}\sum_{i=1}^m(h_\theta(x^i)-y^i)^2 }\cdot x{^{(i)}_j}=\  (for\ j\in[0,n])
$$

----------

#### (2) Feature Scaling

* When the two parameter have a great difference (say size(0-2000 ${feet}^2$),number of bedrooms(1-5)) The contour plots may be **tall and slim** makes it difficult to find the local minimum

* Feature Scaling

  * Use 

  $$
  x_1 = {size(0-2000 {feet}^2)\over2000},x_2={number\ of\ bedrooms\over5}\  (x_1,x_2\in[0,1])
  $$

  * Only needed when the scale is very different

* Mean Normalization

  * Replace $x_i$ with $x_i-\mu_i$ to make features have approximately zero mean (do not apply to $x_0 = 1$)
    $$
    x_1 = {size-1000\over2000},x_2={no. bedrooms-2\over5}
    $$

    $$
    x_i={x_i-\mu_i\over s_i} \ (\mu\ is\ average,s\ is\ range=max-min )
    $$

    

-------------

#### (3) Learning Rate $\alpha$

* two point
  * ***Debugging*** : How to make sure gradient descent is working correctly
  * How to choose $\alpha$
* Debugging use a new function
  * Y-axis : $min J(\theta)$ X-axis: No. of iterations
  * $min J(\theta)$ should decrease after every iteration

----------------

#### (4) Features and Polynomial Regression

* 2 Points

  * choice of features
  * Polynomial Regression

* Defining new features
  $$
  h_\theta(x) = \theta_0+\theta_1*frontage+\theta_2*depth
  $$

  $$
  frongtage*depth =Area=x
  $$

  $$
  h_\theta(x) = \theta_0+\theta_1x
  $$

* Polynomial regression
  $$
  h_\theta(x) = \theta_0+\theta_1x+\theta_2x^2+\theta_3x^3
  $$

  $$
  h_\theta(x) = \theta_0+\theta_1x+\theta_2\sqrt{x}
  $$

  

  > use cubic function because house price will not go down as size increase

  We can simply use
  $$
  h_\theta(x) = \theta_0+\theta_1x_1+\theta_2x_2+\theta_3x_3
  $$

  $$
  x_1=size,\ x_2={size}^2,\ x_3={size}^3
  $$

  Don't forget Feature scaling

------------

### 2. Computing Parameters Analytically

------------

#### (1) Normal Equation

* Solve for $min J(\theta)$ at one step analytically

* Intuition: if 1D ($\theta\inR$)
  $$
  J(\theta)=a\theta^2+b\theta+c
  $$

  $$
  {\delta\over\delta\theta}J(\theta)=...->0
  $$

  But it is too difficult to implement
  $$
  \theta={(X^TX)}^{-1}X^T\vec y
  $$

  * Explain

    $X$ is the training set m*n (m sets of data,n features) $\vec y$ is the right answer

  $$
  X\vec \theta=\vec y\ is\ not\ always\ solvable
  $$

  $$
  We\ find\ a\ similar\ answer\ \theta\ such\ that\ X\hat{\theta}=\vec p
  $$

  $$
  \vec p\ is\ a\ projection\ of\ \vec y\ on\ the\ column\ space\ of\ X,\ to\ make\ it\ solvable
  $$

  $$
  \hat{\theta}=X^{-1}\vec p
  $$

  $$
  \vec p\ and\color{red}{\ column\ space\ of\ X}\ are\ orthogonal\ to\ \vec y-\vec p\Longrightarrow X^T\cdot(\vec y-\vec p)=\vec0\Longrightarrow X^T\cdot(\vec y-X\hat \theta)=0
  $$

  $$
  \hat \theta={(X^TX)}^{-1}X^T\vec y
  $$

  $$
  \vec p=X\vec \theta=X{(X^TX)}^{-1}X^T\vec y=P\vec y\ (P\ is\ the\ projection\ matrix)
  $$

  $$
  P=X{(X^TX)}^{-1}X^T
  $$

  * $P^T=P$, $P^2=P$ 
  * P * Anyone is in the column space of X

* Implementation (no need feature scaling)

  ```octave
  pinv(x'*x)*x'*y
  ```

* Pros

  * No need $\alpha$
  * No need iterate

* Cons : if n is large(features), it is slow [O(n^3) while gradient descent is O(kn^2) fit for(n<10000)]

----------------

#### (2) Normal Equation Noninvertibility

* In octave

  * `pinv()` : pseudo invert (has value even not investable)
  * `inv()`: real invert

* $XX^T$ is not invertable

  * Redundant features	(dependent)

  * To many featrues(e.g. m<=n)

    > Delete some features, or use **regularization**

* 

