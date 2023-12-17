
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
      self.conv1_1=nn.Conv2d(in_channels=3,out_channels=16,kernel_size=3,stride=1,padding=1)
      self.conv1_2=nn.Conv2d(in_channels=16,out_channels=32,kernel_size=3,stride=1,padding=1)
      
      self.conv2_1=nn.Conv2d(in_channels=35,out_channels=32,kernel_size=3,stride=1,padding=1)
      self.conv2_2=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1)
      
      self.conv3_1=nn.Conv2d(in_channels=99,out_channels=128,kernel_size=3,stride=1,padding=1)
      self.conv3_2=nn.Conv2d(in_channels=128,out_channels=256,kernel_size=3,stride=1,padding=1)

      self.relu=nn.ReLU()
      self.max_pool=nn.MaxPool2d()
      
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

      y=self.relu(self.conv3_1(y))
      y=self.relu(self.conv3_2(y))
      y=self.max_pool(y)


      y=y.view(-1,4096)
      y=self.relu(self.fc1(y))
      y=self.relu(self.fc2(y))
      y=self.fc3(y)
      return y
        
```

``` python
class ChannelAttention(nn.Module):

  def __init__(self, channels, reducation):
    super(ChannelAttention, self).__init__()
	self.gap=nn.AdaptiveAvgPool2d((1,1))
	self.conv1=nn.Conv2d(in_channels=channels, out_channels=channels//reducation,kernel_size=1)
    self.conv2=nn.Conv2d(in_channels=channels//reducation,out_channels=channels,kernel_size=1)
    self.relu=nn.ReLU()
    self.sigmoid=nn.Sigmoid()

  def forward(self,x):
	ca_out=self.gap(x)
	ca_out=self.relu(self.conv1(ca_out))
	ca_out=self.sigmoid(self.conv2(ca_out))
	ca_out=self.ca_out.expend_as(x)
    y=x*ca_out
    return y

```