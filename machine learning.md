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

#### 2. Gradient Descent Intuition

* first suppose $ \theta_0 = 0 $
  * Use $  \alpha {\delta\over\delta\theta_j }J(\theta_0 , \theta_1)  $ if delta \<(\>) 0 then go right(left) , when =0 stop
  * $\alpha$: small->slow large->fail to converge