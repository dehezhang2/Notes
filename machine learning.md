# Machine Learning

---------------



-------------

## Week1

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
  * Unsupervised learning : 
    * Data has no label (clustering algorithm)
  * Reinforcement learning
  * recommender systems

  

  ----------------------

  ### Model and Cost Function

  #### Model representation

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

    * $ \theta $ is parameter and the function represent a line



