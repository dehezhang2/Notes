





# Machine Learning

---------------



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

* Matrix in Matlab/Octave 

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

* for $ \vec{x}=[x_1;x_2;...;x_n] $ , we use matrix to find $\theta_0, \theta_1$
  $$
  \begin{bmatrix}1&x_1\\1&x_2\\\vdots&\vdots\\1&x_m\\\end{bmatrix}\cdot\begin{bmatrix}\theta_0\\\theta_1\end{bmatrix}=\begin{bmatrix}y_1\\y_2\\\vdots\\y_m\end{bmatrix}
  $$

  -------

  ## Week 2

  --------------

  ### 1. Multivariate Linear Regression

  ------------

  #### (1) Multiple Features

* Features -> {$x_1,x_2,...,x_n$} -> $y$ -> Price

* Notation:

  * $n$ = number of features
  * $x^{(i)}$ = input (features) of $i^{th}$ training example
  * ${x^{(i)}}_j$ = value of feature $i$ in $i^{th}$ training example