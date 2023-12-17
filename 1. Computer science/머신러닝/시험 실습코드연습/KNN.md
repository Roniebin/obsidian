---
tags: ComputerScience, 머신러닝
---
# KNN

``` python

def L2_distance(x1,x2):
   return np.sqrt(np.sum((x1-x2)**2))

class KNN: # 모델이아니기때문에 그냥 매개변수값 저장만 해도됨
  def __init__(self, k=3):
	self.k=k


  def fit(self, X, y): # 테스트데이터로 들어오는거?
      self.X_train=X
      self.y_train=y

  def predict(self,X):
	  y_pred=[]

      for X_i in X:
         distance=[L2_distance(X_i,X_train) for X_train in self.X_train]
		 k_idx=np.argsort(distance)[:self.k]
		 k_labelss=[self.y_train[i] for i in k_idx]
		 most_class=max(k_labels,key=k_lables.count)
		 y_pred.append(most_class)

   return y_pred

```



--------------

``` python
def L2_distance(x1, x2):
  return np.sqrt(np.sum((x1 - x2) ** 2))

class KNN: # 모델이아니기때문에 그냥 매개변수값 저장만 해도됨

  def __init__(self, k=3):
     self.k=k

  def fit(self, X, y): # 테스트데이터로 들어오는거?
	self.X_train=X
	self.y_train=y
  

  def predict(self, X):
    # Prediction
    y_pred=[]

	for X_i in X:
	  distance=[L2_distance(X_i,X_train) for X_train in self.X_train]
	  k_idx=np.argsort(distance)[:self.k]
	  k_labels=[self.y_train[i] for i in k_idx]
	  most_class=max(k_labels,key=k_lables.count)
	  y_pred.append(most_class)

    return y_pred
```