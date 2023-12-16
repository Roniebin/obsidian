```python
class LeNet5(nn.Module):
  def __init__(self):
    super(LeNet5, self).__init__()
    # 신경망 파라미~~터 초기화 (Conv 2개, FC 3개, ReLU, MaxPool)
    self.conv1=nn.Conv2d(in_features=1,out_features=6,karnel_size=5,stride=1,padding=0)
	self.relu=nn.ReLU()
	self.max_Pool=nn.MaxPool2d()
    self.conv2=nn.Conv2d(in_features=6,out_features=16,karnel_size=5,stride=1,padding=0)

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