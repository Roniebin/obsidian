---
tags: ComputerScience, 머신러닝
---
```python
class LeNet5(nn.Module):
  def __init__(self):
    super(LeNet5, self).__init__()
    # 신경망 파라미~~터 초기화 (Conv 2개, FC 3개, ReLU, MaxPool)
    self.conv1=nn.Conv2d(in_channels=1,out_channels=6,karnel_size=5,stride=1,padding=0)
	self.relu=nn.ReLU()
	self.max_Pool=nn.MaxPool2d()
    self.conv2=nn.Conv2d(in_channels=6,out_channels=16,karnel_size=5,stride=1,padding=0)

	self.fc1=nn.Linear(in_features=256,out_featrues=120)
	self.fc2=nn.Linear(in_features=120,out_featrues=84)
	self.fc3=nn.Linear(in_features=84,out_featrues=10)
 
  def forward(self, x):
	  y=self.relu(self.conv1(x))
	  y=max_Pool(y)

	  y=self.relu(self.conv2(y))
	  y=max_Pool(y)

	  y=y.view(-1,256)

	  y=self.relu(self.fc1(y))
	  y=self.relu(self.fc2(y))
	  y=self.relu(self.fc3(y))

    return y
```


# CIFAR10

``` python

class LeNet5(nn.Module):

 def __init__(self):

    super(LeNet5, self).__init__()

    # 신경망 파라미터 초기화 (Conv 2개, FC 3개, ReLU, MaxPool)
    self.conv1=nn.Conv2d(in_channels=3,out_channels=6,kernel_size=5,stride=1,padding=0)
    self.conv2=nn.Conv2d(in_channels=6,out_channels=16,kernel_size=5,stride=1,padding=0)

	self.max_pool=nn.MaxPool2d(2,2)
	self.relu=nn.ReLU()

	self.fc1=nn.Linear(in_features=400,out_features=120)
	self.fc2=nn.Linear(in_features=120,out_features=84)
	self.fc3=nn.Linear(in_features=84,out_features=10)

 def forward(self,x):
	 y=self.conv1(x)
	 y=self.relu(y)
	 y=max_pool(y)
	
	 y=self.conv2(y)
	 y=self.relu(y)
	 y=max_pool(y)
	
	 y=y.view(-1,400)
	
	 y=self.fc1(y)
	 y=self.relu(y)
	
	 y=self.fc2(y)
	 y=self.relu(y)
	
	 y=self.fc3(y)
	 y=self.relu(y)

 return y


```

--------------

``` python
class LeNet5(nn.Module):

  

  def __init__(self):

    super(LeNet5, self).__init__()

    # 신경망 파라미터 초기화 (Conv 2개, FC 3개, ReLU, MaxPool)

	self.conv1=nn.Conv2d(in_channels=1,out_channels=6,kernel_size=5,stride=1,padding=0)
	self.conv2=nn.Conv2d(in_channels=6,out_channels=16,kernel_size=5,stride=1,padding=0)
	self.relu=nn.ReLU()
	self.max_pool=nn.MaxPool2d(2,2)
	self.avg_pool=nn.AvgPool2d(2,2)

    self.fc1=nn.Linear(in_features=256,out_feautures=120)
    self.fc2=nn.Linear(in_features=120,out_feautures=84)
    self.fc3=nn.Linear(in_features=84,out_feautures=10)
  

  def forward(self, x):

    #-----------------------------------------------------------------
     y=self.conv1(x)
     y=self.relu(y)
     y=self.max_pool(y)
 
	 y=self.conv2(y)
     y=self.relu(y)
     y=self.max_pool(y)

     y=y.view(-1,256)
     
     y=self.relu(self.fc1(y))
     y=self.relu(self.fc2(y))
     y=self.relu(self.fc3(y))

    #-----------------------------------------------------------------



    #-----------------------------------------------------------------
  

    #-----------------------------------------------------------------

  

    return y
```