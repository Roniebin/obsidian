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

```python
def L2_distance(x1, x2):
	return np.sqrt(np.sum((x1-x2)**2))
  

class KNN: # 모델이아니기때문에 그냥 매개변수값 저장만 해도됨

  def __init__(self, k=3):
    self.k=k
    # initialization

  def fit(self, X, y): # 테스트데이터로 들어오는거?
     self.X_train=X
     self.y_train=y

  def predict(self,X):
     y_pred=[]
     
     for X_i in X:
        distance=[L2_distance(X_i,X_train)for X_train in self.X_train]
        k_idx=np.argsort(distance)[:self.k]
        k_labes=[self.y_train[i] for i in k_idx]
        most_class=max(k_labels,key=k_labels.count)
		y_pred.append(most_class)
		reutrn y_pred
```


```python
class SVM:

    def __init__(self, learning_rate=0.001, n_iters=1000):

        # iitialization

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
		         self.b-=lr*y_[idx]

    def predict(self, X):
		prediction=np.dot(X,self.w)+self.b
		prediction=np.sign(prediction)
		return prediction
     
```

``` python
class SVM:

    def __init__(self, learning_rate=0.001, n_iters=1000):

        # initialization
        self.lr=learning_rate
        self.n_iters=n_iters
        self.w=None
        self.b=None

    def fit(self, X, y):
        # Update parameters
		y_=np.where(y<=0,-1,+1)
		n_samples,n_features=X.shape
		self.w=np.zeros(n_features)
		self.b=0
		for i in range(self.n_iters):
		   for idx,x_i in enumerate(X):
		      condition=y_[idx]*(np.dot(x_i,self.w)+self.b)>=1
		      if not condition:
		         self.w-=lr*(-np.dot(x_i,y_[idx]))
		         self.b-=lr*(-y[idx])  

    def predict(self, X):
      prediction=np.dot(X,self.w)+self.b
      prediction=np.sign(prediction)
      return perdiction

    
```