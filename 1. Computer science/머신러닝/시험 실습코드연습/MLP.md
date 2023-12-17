---
tags: ComputerScience, 머신러닝
---
# Single layer perceptron

```python
class SLP(nn.Module):

  def __init__(self):
    super(SLP, self).__init__()
    self.fc=nn.Linear(in_features=784,out_features=10)

  def forward(self, x):
	  x=x.view(-1,28*28)
	  y=self.fc(x)

	  return y
```


``` python
class MLP(nn.Module):
  def __init__(self):
    super(MLP, self).__init__()
	self.fc1=nn.Linear(in_features=784,out_features=300)
	self.fc2=nn.Linear(in_feaures=300,in_features=10)

	self.sigmoid=nn.Sigmoid()
	self.relu=nn.ReLU()
 

  def forward(self, x):
	x=x.view(-1,28*28)
	y=self.relu(self.fc1(x))
	y=self.relu(self.fc2(y))

	return y

  
```

# Perceptron 학습을 위한 반복문

```python
for epoch in range(training_epochs):
  avg_cost = 0
  total_batch = len(data_loader)


  for img, label in data_loader:
    pred=network(img)
    loss=loss_function(pred,label)
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()

    avg_cost += loss / total_batch


  print('Epoch: %d Loss = %f'%(epoch+1, avg_cost))
```


---------------------------
# 두번째 빽빽이

# single layre perceptron

```python

class SLP(nn.Module):

  def __init__(self):
    super(SLP, self).__init__()
    self.fc=nn.Linear(in_features=784,out_features=10)
  

  def forward(self, x):
     x=x.view(-1,28*28)
     y=self.fc(x)
     return y

```


``` python
class MLP(nn.Module):

  def __init__(self):
    super(MLP, self).__init__()
		self.fc1=nn.Linear(in_features=784,out_features=300)
		self.fc2=nn.Linear(in_features=300,out_featuers=10)
		self.sigmoid=nn.Sigmoid()
		self.relu=nn.ReLU()

  def forward(self, x):
	x=x.view(-1,784)
	y=self.fc1(x)
	y=self.relu(y)
	
	y=self.fc2(y)
	y=self.relu(y)
    return y
```

----------------

# 세번째

# single

``` python
class SLP(nn.Module):

  def __init__(self):

    super(SLP, self).__init__()
	self.fc=nn.Linear(in_features=784,out_features=10)
	

  def forward(self, x):
	x=x.view(-1,784)
	y=self.fc(x)
	return y
```

# Multi

``` python
class MLP(nn.Module):

  
  def __init__(self):
	self.fc1=nn.Linear(in_feautres=784,out_features=300)
	self.fc2=nn.Linear(in_features=300,out_features=10)
	  
    self.sigmoid=nn.Sigmoid()
    self.relu=nn.ReLU()
  def forward(self, x):
	x=x.view(-1,784)
	y=self.relu(self.fc1(x))
	y=self.relu(self.fc2(y))
  

```