













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
    J_history = zeros(num_iters, 1);
    theta = theta - (1/length(y))*alpha*X'*(X*theta-y);
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

    