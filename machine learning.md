













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
      * Every circle represent same value of $ J(\theta_0, \theta_1)  ​$ (等高线, 3-D 图的投影)

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
\theta_j:= \theta_j -\alpha {{1\over{m}}\sum_{i=1}^m(h_\theta(x^i)-y^i) }\cdot x{^{(i)}_j}=\  (for\ j\in[0,n])
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
  * How to choose $\alpha​$
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

* Intuition: if 1D ($\theta \in R$)
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
  \vec p=X\hat \theta=X{(X^TX)}^{-1}X^T\vec y=P\vec y\ (P\ is\ the\ projection\ matrix)
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

  * No need $\alpha​$
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



-------------

### 3. Ocatave/Matlab Tutorial

-----------

#### (1) Basic operations

----------

```octave
1~=2 		%not equal sign
xor(1,0)	%yihuo
1&&0		%AND
1 || 0 		%or
PS1("somestring");	%change the string in front of command line
x = 3;		%semicolon supressing output(not print the answer)
a=pi
disp(a);	%display
disp(sprintf('2 decimals: %0.2f',a))	%display in two decimal place
v=1:0.1:2	%quick way to get row vector from 1 to 2 every column increase 0.1
v=1:6		%from 1 to 6 increase 1 by default
w=ones(2,3)	%all entries is 1
w=zero(2,3)
w=rand(2,3)
w=randn(1,3)%Gaussian distribution
w = -6+sqrt(10)*(randn(1,10000));
hist(w)		%draw histogram
hist(w,50)	%histogram with 50 bins
eye(4)		%4by4 identity matrix
help eye
help rand	%show the detail of method

```

#### (2) Moving Data Around

```octave
sz=size(A)	% show size of matrix sz is also a matrix
size(A,1)	% row of A
size(A,2)	% column of A
length(A)	% longer dimention max(m,n)
pwd			% current path you are in
cd			% change the pass
ls			% list the file
load featureX.dat	%load the file
load('featuresX.dat')
who			% show all the variables
whos		% show in detail
clear featuresX	%delete the variable
v = priceY(1:10)	% store first 10 columns of priceY in the v
save hello.mat v	%save v in the new file
save hello.txt v-ascii	%save as txt
A(3,2)		%i=3,j=2 elements of A
A(2,:)		%: means the whole row or column
A([1 3],:)	%all 1 rows and 3 rows
A(:,2)=[10;11;12]	%assign
A=[A,[100;101;102]]	%add a column
A(:)				%put all elements of A into a single vector

```

#### (3) Computing on Data

```octave
A.*B	%get matrix c that c(i,j)=a(i,j)*b(i,j)
v = [1;2;3]
1./v	%get matrix c that c(i,j) = 1/a(i,j)
log(v)
exp(v)
abs(v)	% similar
% add 1 to every entries
v+1
v+ones(length(v),1)	
A'	% A transpose
A = [1 15 2 0.5]
val = max(A)	% biggest number
max(A,[],1)
max(A,[],2)		% row and col max respectively
[val,ind]=max(a)% assign the position to ind
A < 3			% return true or false as a matrix
find(A<3)		% return all true entrys
A = magic(3)	% all the rows and columns are diagonals sum to a same number
[r,c]=find(A>=7)% A(ri,ci)>=7
sum(A)			% add all colmn or row for m = 1 matrix
sum(A,1)		% sum all the row
sum(A,2)		% sum all the col
sum(sum(A.*eyes(size(A),1)))	% sum the diagnal of one side
sum(sum(A.*flipud(eyes(size(A),1)))	% sum the diagnal of other side
prod(A)			% multiple
floor(A)		
ceil(A)			%for all entries


```

#### (4) Plotting Data

```octave
plot(t,y1)		% t-x axis y-y axis
plot(t,y2,'r')	% print y2 in a different color
xlabel('time')
ylabel('value')
legend('sin','cos')
title('my plot')
cd 'your path'; print -dpng 'myPlot.png'

% plot in different pictures
figure(1); plot(t,y1);
figure(2); plot(t,y2);

% Divides plot a 1*2 gird, access first element
subplot(1,2,1);	
plot(t,y1);
subplot(1,2,2);
plot(t,y2);
axis([0.5 1 -1 1])	%change range of x and y
clf;				% clear figure
A = magic(5);
imagesc(A);			%represent in different colors
% present the color bar and use black white style
imagesc(A),colorvar,colormap gray;

```

#### (5) Control Statement : `for` `while` `if`

```octave
% for loop
v = zeros(1,10)
for i = 1:10,
	v(i) = 2*i;
end;
% or
indicies = 1:10;
for i = indicies,
	disp(i);
end;
% while loop
i = 1;
while i<=5,
	v(i++) = 100;
end;
% or
i = 1;
while true,
	v(i++) = 99;
	if i == 6,
		break;
	end;
end;
% if - else
if v(1) == 1,
	disp('The value is one');
elseif v(1) == 2,
	disp('The value is two');
else
	disp('The value is not one or two');
end;


```

* Create Function

  * Create a new file named as 'the name of function.m'

  ```octave
  function y = squareThisNumber(x)
  y = x^2;
  % use
  addpath('path of the function')
  squareThisNumber(5)
  
  function [y1,y2] = squreAndCubeThisNumber(x)
  y1 = x^2;
  y2 = x^3;
  
  ```

  * $J(\theta)$ in the exmaple

    ```octave
    % use the function
    >> x = [1 1;1 2;1 3]
    >> y = [1;2;3]
    >> theta = [0;1];
    
    ```

    ```octave
    % the function file 'costFunctionJ'
    function J = costFunctionJ(X,y,theta)
    m = size(X,1)
    predictions = X*theta; 				% m*2 . 2*1
    sqrErrors = (predictions-y).^2;		% turn every entries into its square
    
    J = 1/(2*m)*sum(sqrErrors);
    
    ```

    

#### (6) Vectorization

$$
h_\theta (x) = \sum{^n_{j=0}}\theta_jx_j=\theta^TX
$$

* silly version

  ```octave
  prediction = 0.0;
  for j=1:n+1,
  	prediction = prediction + theta(j)*X(j);
  end;
  ```

  

* Vectorized version

  ```octave
  prediction = theta'*X;
  ```

$$
\theta_j:= \theta_j -\alpha {{1\over{m}}\sum_{i=1}^m(h_\theta(x^i)-y^i) }\cdot x{^{(i)}_j}=\  (for\ j\in[0,n])
$$

* Implementation

  ```octave
  prediction = X*theta; 	% (m,1)
  Error = prediction - Y;	% (m,1)
  delta = (1/m)*X'*Error;		% (n+1,m)*(m,1)=(n+1,1)
  theta=theta-alpha*delta;
  
  theta = theta-alpha*X'*(X*theta-Y)
  ```

  

#### (7) Method learnt in the assignment

```octave
data = load('filename');	% open the file and store it as a matrix
linspace - 生成线性间距向量

    此 MATLAB 函数 返回包含 x1 和 x2 之间的 100 个等间距点的行向量。

    y = linspace(x1,x2)
    y = linspace(x1,x2,n)


logspace - 生成对数间距向量

    此 MATLAB 函数 生成一个由在 10^a 和 10^b（10 的 N 次幂）之间的 50 个对数间距点组成的行向量 y。logspace
    函数对于创建频率向量特别有用。该函数是 linspace 和:运算符的对数等价函数。

    y = logspace(a,b)
    y = logspace(a,b,n)
    y = logspace(a,pi)
```

* plot

  ```octave
  % two axis of 100 grids from (-10,10) (-1,4) respectively
  theta0_vals = linspace(-10,10,100);
  theta1_vals = linspace(-1,4,100);
  % draw the graph
  J_vals = zeros(length(theta0_vals),length(theta1_vals));
  % Fill
  for i = 1:length(theta0_vals)
  	for j = 1:length(theta1_vals)
  		t = [theta0_vals(i);theta1_vals(j)];	%a pair of theta
  		J_vals(i,j) = computeCost(x,y,t);
  	end
  end
  % Surface plot
  figure;
  surf(theta0_vals, theta1_vals, J_vals)
  xlabel('\theta_0'); ylabel('\theta_1');
  
  % Contour plot
  figure;
  % Plot J_vals as 15 contours spaced logarithmically between 0.01 and 100
  contour(theta0_vals, theta1_vals, J_vals, logspace(-2, 3, 20))
  xlabel('\theta_0'); ylabel('\theta_1');
  hold on;
  plot(theta(1), theta(2), 'rx', 'MarkerSize', 10, 'LineWidth', 2);
  ```

* Normalization for multiple features

  ```octave
  % normalization : after normalize you need to store the mean and standard(when predict new value we need to change its scale again)
  mean(X);	% return average of each column
  std(X);		% return standard deviation of each column
  repmat(A,m,n)	% treat A as an element create a matrix m by n of A as a entry
  % the code
  X_norm = X;
  mu = zeros(1, size(X, 2));
  sigma = zeros(1, size(X, 2));
  mu = mean(X)
  X_norm = X_norm-repmat(mu,size(X,1),1)
  sigma = std(X)
  X_norm = X_norm./repmat(sigma,size(X,1),1)
  ```

* Gradient Descent for multiple features

  * cost function

  ```octave
  function J = costFunctionJ(X,y,theta);
  J = 1/(2*size(X,1))*((X*theta-y)'*(X*theta-y));
  ```

  * Gradient iteration

    ```octave
    function [theta, J_history] = gradientDescentMulti(X, y, theta, alpha, num_iters);
    % Create a column vector of J
    J_history = zeros(num_iters, 1);
    % do gradient descent
    theta = theta - (1/length(y))*alpha*X'*(X*theta-y);
    % compute new J for debug
    J_history(iter) = computeCostMulti(X, y, theta);
    end
    ```

  * Normal Equation

    ```octave
    function [theta] = normalEqn(X, y)
    theta = zeros(size(X, 2), 1);
    theta = pinv(X'*X)*X'*y;
    end
    ```

------------

## Week 3

-----------

### 1. Classification -> logistic regression

* Email: spam/not spam

* Online Transactions: Fraudulent ( Yes/ No )

* Tumor: Malignant / Benign

  $y\in\ \{0,1\}$ 0: "Negative Class"; 1: "Positive Class"

* Why not use linear regression? : It is easily affected by noisy points

--------

### 2. Hypothesis Representation (function used)

#### (1) Logistic Regression Model

Want $0\leq h_\theta(x)\leq 1$ 
$$
h_\theta(x)=g({\theta}^Tx)={1\over{1+e^{-{\theta}^Tx}}}
$$

$$
g(z) = {1\over{1+e^{-z}}}
$$

g is Sigmoid (Logistic) function

#### (2) Interpretation of Hpothesis Output

 $h_\theta (x)=$ estimated probability that y =1 on input x = $P(y=1\ |\ x;\theta)$

$h_\theta (x)=0.7$ => Tell patient that 70% chance of tumor being malignant
$$
P(y=0\ |\ x;\theta)=1-P(y=1\ |\ x;\theta)
$$

#### (3) Decision Boundary

* property of the g 

  * Suppose predict "y=1" if $h_ \theta(x) \geq0.5$  
  * Predict "y=0" if $h_\theta(x)<0.5$                  
  * $g(z)\geq0.5$ when $z\geq0$  ( ${\theta}^Tx\geq0$ )

* Decision Boundary
  $$
  h_\theta (x) = g (\theta_0+\theta_1x_1+\theta_2x_2)
  $$
  

$$
\theta = [-3,1,1]
$$

​	Predict "y=1" if $-3+x_1+x_2\geq0$ $x_1+x_2=3$ is a line (Decision boundary)

​	Cut the $x_1x_2$ plane into two pieces 

* What if the training set is more complex (cannot use a line) : Add polynomial parameter

--------------

### 3. Logistic Regression Model

#### (1) Cost function

* Problem

  Training set: {$(x^{(1)},y^{(1)}),(x^{(2)},y^{(2)}),\ ...\ ,(x^{(m)},y^{(m)})$}

  m examples: $x\in[x_0,x_1,\ ...\ x_n]\ x_0=1, y\in\{0,1\}$

  $h_\theta(x) = {1\over1+e^{-{\theta}^Tx}}$ 

  How to choose $\theta$ 

* Logistic regression cost function
  $$
  Cost(h_\theta(x),y)=
  \begin{cases}
  -log(h_\theta(x))\ if\ y=1 \\
  -log(1-h_\theta(x))\ if\ y=0\\
  \end{cases}
  $$

  * If $y=1,\ h_\theta(x) = 1$ then Cost = 0
  * But as $h_\theta(z)\rightarrow0$ ,$Cost\rightarrow\infin$
  * 如果猜对了， 奖励这个算法， 猜错了则增大cost

#### (2) Simplified cost function and gradient descent

$$
J(\theta)={1\over m}\sum^m_{i=1}Cost(h_\theta(x^{(i)},y^{(i)})
$$

$$
Cost(h_\theta(x),y)=
\begin{cases}
-log(h_\theta(x))\ if\ y=1 \\
-log(1-h_\theta(x))\ if\ y=0\\
\end{cases}
$$

Note y =0 or 1 always
$$
Cost(h_\theta(x),y)=-ylog(h_\theta(x))-(1-y)log(1-h_\theta(x)))
$$

$$
J(\theta)=-{1\over m}\sum^m_{i=1}[y^{(i)}log(h_\theta(x^{(i)}))+(1-y^{(i)})log(1-h_\theta(x^{(i)}))]
$$

* Gradient Descent

  $\theta_j:=\theta_j-\alpha{\delta\over{\delta\theta_j}}J(\theta)$

  Repeat{

  $\theta_j:=\theta_j-\alpha{1\over m} \sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})x^{(i)}_j$

  }
  $$
  {\delta\over{\delta\theta_j}}J(\theta)={1\over m} \sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})x^{(i)}_j
  $$
  

Which is similar to linear regression

#### (3) Advanced optimization

Given $\theta$ we have code that can compute $J(\theta)$ and  ${\delta\over{\delta\theta_j}}J(\theta)$ 

* Optimization algorithm

  * Conjugate gradient
  * BFGS
  * L-BFGS
  * Advantages
    * No need to manually pick $\alpha$
    * Often faster than gradient descent
  * Disadvantages
    * More complex 

* Example (Use derivative)

  $\theta = [\theta_1,\theta_2]$

  $J(\theta)=(\theta_1-5)^2+(\theta_2-5)^2$

  ${\delta\over\delta\theta_1}J(\theta)=2(\theta_1-5)$

  ${\delta\over\delta\theta_2}J(\theta)=2(\theta_2-5)$

```matlab
function [jVal,gradient] = costFunction(theta)
jVal = (theta(1)-5)^2+(theta(2)-5)^2;
gradient = zero(2,1);
gradient(1) = 2*(theta(1)-5);
gradient(2) = 2*(theta(2)-5);
```

```matlab
% option is a data structure which can store your options
options = optimset('GradObj','on','MaxIter','100');
% set gradient objective parameter to on, and set the maximum number of interation
initialTheta = zero(2,1);
% @represent a pointer to costFunction
[optTheta,functionVal,exitFlag] = fminunc(@costFunction,initialTheta,options);
```

-----------

### 4. Multi-class classification: one-vs-all

* Multiclass classification

  * Email folding/tagging: Work, friend, family, hobby
  * Medical: Not ill, cold, flu
  * Weather: Sunny,Cloudy,Rain,Snow

* One-vs-all (one-vs-rest) : use more binary classification
  $$
  h_\theta^{(i)}(x)  = P(y=i|x;\theta) (i=1,2,3)for\ three\ cluster
  $$

* On a new x, to make a prediction, pick the class i that maximizes $max\ h_\theta^{(i)}(x)$ 

------------

### 5. Solving the problem of overfitting

#### (1) The problem of overfitting

* Three kinds of fitting

  * Cannot fit very well => "Underfit" or "High bias" (偏见，偏差)
  * Fit well => "Just right"
  * 100% fitting (Although fitting, but the curve is meaningless) => "Overfit" "High variance"

* Overfitting : If we have too many features, the learned hypothesis may fit the training set very well ($J(\theta)={1\over {2m}}\sum_{i=1}^m(h_\theta(x^{(i)}-y^{(i)})^2\approx0$), but fail to generalize to new examples (predict prices on new examples)

* Addressing overfitting:

  * draw the graph

  * Options

    (1) Reduce number of features

    * Manually select which features to keep
    * Model selection algorithm

    (2) Regularization

    * Keep all the features, but reduce magnitude/values of parameters $\theta_j$ 
    * Works well when we have a lot of features, each of which contributes a bit to predicting $y$ .

#### (2) Cost function

* modify the cost function by add quadratic of overfitting $\theta$ , and recalculate the minimum, to make them contribute less than before

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/j0X9h6tUEeawbAp5ByfpEg_ea3e85af4056c56fa704547770da65a6_Screenshot-2016-11-15-08.53.32.png?expiry=1535587200000&hmac=pTJpk1gxb2Iihrs1iyuawu2XC1jluYbc9E76biX1m3Q),

* Regularization : small value for parameters $\theta_0,\theta_1,...,\theta_n$

  * "Simpler" hypothesis
  * Less prone to overfitting
  * In real use, we don't know to shrink which parameter => shrink all parameters ($\lambda$ is regularization parameter)

  $$
  J(\theta)={1\over2m}[\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})^2+\lambda\sum_{j=1}^n{\theta_j}^2]
  $$

  * If $\lambda$ is too large => cause underfitting ( i.e. $h_\theta(x)=\theta_0$) 

#### (2) regularized linear regression

* Gradient descent (with regularization) => treat $\theta_0$ differently

  Repeat{

  $\theta_0:=\theta_0-\alpha{1\over m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})x_0^{(i)}$

  $\theta_j:=\theta_j-\alpha{1\over m}[\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})x_j^{(i)}+\lambda\theta_j](j\neq0)$

  Or $\theta_j:=\theta_j(1-\alpha{\lambda\over m})-\alpha{1\over m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})x_j^{(i)}(j\neq0)((1-\alpha{\lambda\over m})\ is\ always\ less\ than\ 1)$

  }

* Normal equation
  $$
  \theta=(X^TX+\lambda L)^{-1}X^T y
  $$
  Where L is a matrix
  $$
  \begin{bmatrix}0&0&\cdots&0\\0&1&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&1 \end{bmatrix}
  $$

  * Use when the matrix $X^TX$ is singular



#### (3) regularized logistic regression

* Cost function
  $$
  J(\theta)=-[{1\over m}\sum^m_{i=1}[y^{(i)}log(h_\theta(x^{(i)}))+(1-y^{(i)})log(1-h_\theta(x^{(i)}))]]+{\lambda\over2m}\sum^n_{j=1}{\theta_j}^2 (j=1,2,...,n)
  $$

* Advanced optimization



-------------

## Week4

### 1. Motivations

* There may be a lot of features => it is not efficient to use all feature
* Neural network => build brain

-----------

### 2. Neural Networks

#### (1) Model Representation I

* Neuron model : logistic unit

  
  $$
  \begin{bmatrix}x_0\\x_1\\\vdots\\x_m\end{bmatrix}=>[\ \ ]=>h_\theta(x)
  $$

  * Sigmoid function => activation function $g(z)$ 
  * $\theta$ => weights or parameters

* Neuron network

  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/0rgjYLDeEeajLxLfjQiSjg_0c07c56839f8d6e8d7b0d09acedc88fd_Screenshot-2016-11-22-10.08.51.png?expiry=1535932800000&hmac=5jlI2pmR-1O8ekWJG_xQU9DzH75VYHo1nEGwRfcALv4)

  * dimension of $\Theta$ : $s_{j+1}*(s_j+1)$ where $s_n$ is the number of variables in nth layer

#### (2) Model representation II

* Forward propagation: Vectorized implementation

$$
z^{(j+1)}={\Theta}^{(j)}a^{(j)}
$$

$$
h_\theta(x)=a^{(j+1)}=g(z^{(j+1)})
$$

-----------------

### 3. Applications

#### (1) Example and Intuitions I



![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/wMOiMrGnEeajLxLfjQiSjg_bbbdad80f5c95068bde7c9134babdd77_Screenshot-2016-11-23-10.07.24.png?expiry=1535932800000&hmac=pM3HSrJVUvTS0FU0xp8PM9V4ydfbbshgC5Ojkw282uw)

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/f_ueJLGnEea3qApInhZCFg_a5ff8edc62c9a09900eae075e8502e34_Screenshot-2016-11-23-10.03.48.png?expiry=1535932800000&hmac=2F8_rvXgjCmIfPhfKewJ4Y42p7jyqwo6bazC8umkxcM)

#### (2) Example and Intuitions II

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/rag_zbGqEeaSmhJaoV5QvA_52c04a987dcb692da8979a2198f3d8d7_Screenshot-2016-11-23-10.28.41.png?expiry=1535932800000&hmac=NLVJU-uxcwUqyc1Zz5_Z-ZMQpTZHwBiy8zujyg-lZWU)

-----------

## Week 5

-----

### 1. Cost Function and Backpropagation

#### (1) Cost function

* Cost functions

  * Denotes
    * $L$ = total number of layers in the network
    * $S_l$ = number of units (not counting bias unit) in layer $l$
    * $K$ = number of output units/classes
  * Logistic regression

  $$
  J(\theta)=-[{1\over m}\sum^m_{i=1}[y^{(i)}log(h_\theta(x^{(i)}))+(1-y^{(i)})log(1-h_\theta(x^{(i)}))]]+{\lambda\over2m}\sum^n_{j=1}{\theta_j}^2 (j=1,2,...,n)
  $$

  * Neural network (for multi-class problem there are K clusters) $h_\Theta(x) \in R^K\ (h_\Theta(x))_i=i^{th}\ output$
    * The first part add the cost of all the m-by-K results
    * The second part add all the theta used (every column, row, layer (L))

$$
J(\Theta)=-{1\over m}[\sum_{i=1}^m\sum_{k=1}^Ky^{(i)}_klog(h_\Theta(x^{(i)}))_k+(1-y^{(i)}_k)log(1-h_\Theta(x^{(i)}))_k]+{\lambda \over 2m}\sum_{l=1}^{L-1}\sum_{i=1}^{S_l}\sum_{j=1}^{S_{l+1}}(\Theta_{ji}^{l})^2
$$

#### (2) Backpropagation Algorithm

* Gradient computation

  * we need : $min_\Theta J(\Theta)$ and ${\delta\over\delta\Theta^{(l)}_{ij}}J(\Theta)$ 

  * Given one training example $(x, y)$ 

  * Intuition: $\delta^{(l)}_j$ = "errors" of node $j$ in layer $l$ 
    $$
    \delta_j^{(4)}=a^{(4)}_j-y_j
    $$


$$
\delta^{(3)}=(\Theta^{(3)})^T\delta^{(4)}.*\ (a^{(3)}.*(1-a^{(3)}))
$$

$$
\delta^{(2)}=(\Theta^{(2)})^T\delta^{(3)}.*\ (a^{(2)}.*(1-a^{(2)}))
$$

$$
{\delta\over\delta\Theta_{ij}^{(l)}}J(\Theta)=a^{(l)}_j\delta^{(l+1)}_i
$$

* Backpropagation algorithm

  * Training set $\{(x^{(1)},y^{(1)}),...,(x^{(m)},y^{(m)})\}$

  * Set $\Delta^{(l)}_{ij}=0$ (for all l, i, j)

    For i=1 to m

    ​	Set $a^{(1)} = x^{(i)}$

    ​	Perform forward propagation to compute $a^{(l)}$ for $l=2,3,...,L$

    ​	Using $y^{(i)}$, compute $\delta^{(L)}=a^{(L)}-y^{(i)}$

    ​	Compute $\delta^{(L-1)},\delta^{(L-2)}, \delta^{(2)}$  using $\delta^{(l)}=((\Theta^{(l)})^T\delta^{(l+1)}).*a^{(l)}.*(1-a^{(l)})$

    ​	 $\Delta^{(l)}_{(ij)}+=a^{(l)}_j\delta^{(l+1)}_i$

    ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Ul6i5teoEea1UArqXEX_3g_a36fb24a11c744d7552f0fecf2fdd752_Screenshot-2017-01-10-17.13.27.png?expiry=1536019200000&hmac=15UFuOdaUFnYJHMtyA1CTMY5dwh8f5sI6W1IIwa5YNw)

#### (3) Backpropagation Intuition

* Forward Propagation
  $$
  z^{(l)}_1=\Theta^{(l-1)}_{10}*1+\Theta^{(l-1)}_{11}*a^{(l-1)}_1+\Theta^{(l-1)}_{11}*a^{(l-1)}_2
  $$
  Focusing on a single example $x^{(i)}$ $y^{(i)}$ ignore regularization
  $$
  cost = y^{(i)}logh_\Theta(x^{(i)})+(1-y^{(i)})logh_\Theta(x^{(i)})
  $$
  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/qc309rdcEea4MxKdJPaTxA_324034f1a3c3a3be8e7c6cfca90d3445_fixx.png?expiry=1536019200000&hmac=P1IrwwNA4YtSRAQkhtuB1GL8oA2nH5rtPJhWr73OlWc)

#### (4) Backpropagation in Practice

* 