---
tags: ComputerScience, 머신러닝
---
``` python
class SVM:

    def __init__(self, learning_rate=0.001, n_iters=1000):
        # initialization

		self.lr=learning_rate
		self.n_iters=n_iters
		self.w=None
		self.b=None
    def fit(self, X, y):
	    y_=np.where(y<=0,-1,+1)

		n_samples,n_features=X.shape
        self.w=np.zeros(n_features)
        self.b=0

		for i in range(self.n_iters):
			for idx,x_i in enumerate(X):
				condition=y_[idx]*(np.dot(x_i,self.w)+self.b)>=1

				if not condition:
				  self.w-=lr*(-np.dot(x_i,y_[idx]))
				  self.b-=lr*(-y_[idx])

    def predict(self,X):
       prediction=np.dot(X.self.w)+self.b
       prediction=np.sign(prediction)
       return prediction


```

``` python

margin=2/sqrt(np.dot(model.w.T,model.w))
```



----------------------------
```python
class SVM:

    def __init__(self, learning_rate=0.001, n_iters=1000):
        # initializatio
        self.lr=learning_reate
        self.n_iters=n_iters
        self.w=None
        self.b=None
        
    def fit(self, X, y):
       y_=np.where(y<=0,-1,1)
       n_samples,n_features=x.shape
       self.w=np.zeros(n_features)
       self.b=0

       for i in range(self.n_iters):
          for idx,x_i in enumerate(X):
              condition=y_[idx]*(np.dot(x_i,self.w)+self.b)>=1

			  if not condition:
			    self.w-=self.lr*(-np.dot(x_i,y_[idx]))
			    self.b-=self.lr*(-y_[idx])		   

    def predict(self, X):
       prediction=np.dot(X,self.w)+self.b
       prediction=np.sign(prediction)
		return prediction
		

        

```

``` python

class SVM:

    def __init__(self, learning_rate=0.001, n_iters=1000):
		self.lr=learning_rate
		self.n_iters=n_iters
		self.w=None
		self.b=None
		
  

    def fit(self, X, y):
        # Update parameters
	  y_=np.where(y<=0,-1,1)
	  n_samples,n_features=X.shape
	  self.w=np.zeros(n_features)
	  self.b=0

	  for i in range(n_iters):
	     for idx,x_i in enumerate(X):
	         condition=y_[idx]*(np.dot(x,self.w)+self.b)>=1
			 if not condition:
			    self.w-=lr*(-np.dot(x_i,y_[idx]))
			    self.b-=lr*y_[idx]

    def predict(self, X):
       prediction=np.dot(X,self.w)+b
       prediction=np.sign(prediction)
	   return prediction
class SVM:

    def __init__(self, learning_rate=0.001, n_iters=1000):
        # initialzation
		self.lr=learning_rate
		self.n_iters=n_iters
		self.w=None
		self.b=None
      
    def fit(self, X, y):
        y_=np.where(y<=0,-1,+1)
        # Update parameters
        n_sampels,n_features=X.shape
        self.w=np.zeros(n_features)
        self.b=0
        for i in range(self.n_iters):
           for idx,x_i in enumerate(X):
              condition=y_[idx]*(np.dot(x,self.w)+self.b)>=1
              if not condition:
                 self.w-=lr*(-np.dot(x_i,y_[idx]))
			     self.b-=lr*(-y_[idx])              
        
   def predict(self,X):
     prediction=np.dot(X,self.w)+self.b
     prediction=np.sign(prediction)
     return prediction

```