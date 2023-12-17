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


    self.conv_skip1=nn.Conv2d(in_channels=3,out_channels=32,kernel_size=3,stride=1,padding=1)
    self.conv_skip2=nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,stride=1,padding=1)
    self.conv_skip3=nn.Conv2d(in_channels=64,out_channels=256,kernel_size=3,stride=1,padding=1)

   def forward(self,x):
      skip_y=
      
```