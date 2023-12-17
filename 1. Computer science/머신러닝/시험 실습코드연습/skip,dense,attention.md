
# skip

``` python
class SimplifiedVGG_skip(nn.Module):


  def __init__(self):
    super(SimplifiedVGG_skip, self).__init__()
    
    self.conv1_1=nn.Conv2d(in_channels=3,out_channels=16,kernel_size=3,stride=1,padding=1)
    self.conv1_2=nn.Conv2d(in_channels=16,out_channels=32,kernel_size=3,stride=1,padding=1)

    self.conv2_1=nn.Conv2d(in_channels=32,out_channels=32,kernel_size=3,stride=1,padding=1)
    self.conv2_2=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1)

    self.conv3_1=nn.Conv2d(in_channels=64,out_channels=128,kernel_size=3,stride=1,padding=1)
    self.conv3_2=nn.Conv2d(in_channels=128,out_channels=256,kernel_size=3,stride=1,padding=1)
  
	self.relu=nn.ReLU()
	self.max_pool=nn.MaxPool2d(2,2)

    self.fc1=nn.Linear(in_features=4096,out_features=512)
    self.fc2=nn.Linear(in_features=512,out_features=256)
    self.fc3=nn.Linear(in_features=256,out_features=10)
    

    self.conv_skip1=nn.Conv2d(in_channels=3,out_channels=32,kernel_size=3,stride=1,padding=1)
    self.conv_skip2=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1)
    self.conv_skip3=nn.Conv2d(in_channels=64,out_channels=256,kernel_size=3,stride=1,padding=1)

   def forward(self,x):
      skip_y=self.conv_skip1(x)
      y=self.relu(self.conv1_1(x))
      y=self.relu(self.conv1_2(y))
      y=skip_y+y
      self.max_pool(y)

	  skip_y=self.conv_skip2(y)
      y=self.relu(self.conv2_1(x))
      y=self.relu(self.conv2_2(y))
      y=skip_y+y
      self.max_pool(y)

	  skip_y=self.conv_skip3(y)
      y=self.relu(self.conv3_1(x))
      y=self.relu(self.conv3_2(y))
      y=skip_y+y
      self.max_pool(y)

      y=y.view(-1,4096)
      y=self.relu(self.fc1(y))
      y=self.relu(self.fc2(y))
      y=self.fc3(y)

	  return y
```


-------------
# dense

``` python
class SimplifiedVGG_dense(nn.Module):

  def __init__(self):
    super(SimplifiedVGG_dense, self).__init__()
    self.conv1_1=nn.Conv2d(in_channels=3,out_channels=16,kernel_size=3,stride=1,padding=1)
    self.conv1_1=nn.Conv2d(in_channels=16,out_channels=32,kernel_size=3,stride=1,padding=1)

	self.conv2_1=nn.Conv2d(in_channels=35,out_channels=32,kernel_size=3,stride=1,padding=1)
	self.conv2_1=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1)

	self.conv3_1=nn.Conv2d(in_channels=99,out_channels=128,kernel_size=3,stride=1,padding=1)
	self.conv3_1=nn.Conv2d(in_channels=128,out_channels=256,kernel_size=3,stride=1,padding=1)

    self.relu=nn.ReLU()
    self.max_pool=nn.MaxPool2d(2,2)

    self.fc1=nn.Linear(in_features=4096,out_features=512)
    self.fc2=nn.Linear(in_features=512,out_features=256)
    self.fc3=nn.Linear(in_features=256,out_features=10)

	def forward(self,x):
		dense_y=x
		y=self.relu(self.conv1_1(x))
		y=self.relu(self.conv1_2(y))
		y=torch.cat([y,dense_y],dim=1) 
	    y=self.max_pool(y)

        dense_y=y
        y=self.relu(self.conv2_1(y))
		y=self.relu(self.conv2_2(y))
		y=torch.cat([y,dense_y],dim=1)
		y=self.max_pool(y)

		dense_y=y
        y=self.relu(self.conv3_1(y))
		y=self.relu(self.conv3_2(y))
		y=torch.cat([y,dense_y],dim=1)
		y=self.max_pool(y)

        y=y.view(-1,4096)
        y=self.relu(self.fc1(y))
        y=self.relu(self.fc2(y))
        y=self.fec3(y)
        return y
```


------------

``` python

  

class SimplifiedVGG_skip(nn.Module):


  def __init__(self):

    super(SimplifiedVGG_skip, self).__init__()
    self.conv1_1=nn.Conv2d(in_channels=3,out_channels=16,kernel_size=3,stride=1,padding=1)
    self.conv1_2=nn.Conv2d(in_channels=16,out_channels=32,kernel_size=3,stride=1,padding=1)
     
    self.conv2_1=nn.Conv2d(in_channels=32,out_channels=32,kernel_size=3,stride=1,padding=1)
    self.conv2_2=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1) 
       
    self.conv3_1=nn.Conv2d(in_channels=64,out_channels=128,kernel_size=3,stride=1,padding=1)
	self.conv3_2=nn.Conv2d(in_channels=128,out_channels=256,kernel_size=3,stride=1,padding=1)


    self.relu=nn.ReLU()
    self.max_pool=nn.MaxPool2d(2,2) 


    self.conv_skip1=nn.Conv2d(in_channels=3,out_channles=32,kernel_size=3,stride=1,padding=1)
    self.conv_skip2=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1)
	self.conv_skip3=nn.Conv2d(in_channels=64,out_channels=256,kernel_size=3,stride=1,padding=1)

	self.fc1=nn.Linear(in_features=4096,out_features=512)
	self.fc2=nn.Linear(in_features=512,out_features=256)
	self.fc3=nn.Linear(in_features=256,out_features=10)

  def forward(self,x):
     skip_y=self.conv_skip1(x)
     y=self.relu(self.conv1_1(x))
     y=self.relu(self.conv1_2(y))
     y=y+skip_y
     y=max_pool(y)

	 skip_y=self.conv_skip2(y)
	 y=self.relu(self.conv2_1(x))
     y=self.relu(self.conv2_2(y))
     y=y+skip_y
     y=max_pool(y)

     skip_y=self.conv_skip3(y)
     y=self.relu(self.conv3_1(y))
     y=self.relu(self.conv3_2(y))
     y=y+skip_y
     y=max_pool(y)

     y=y.view(-1,4096)
     
	 y=self.relu(self.fc1(y))
	 y=self.relu(self.fc2(y))
	 y=self.fc3(y)
	 return y
```

``` python
class SimplifiedVGG_dense(nn.Module):
    def __init__(self):
      super(SimplifiedVGG_dense, self).__init__()

      
  

    def forward(self,x):

        
```