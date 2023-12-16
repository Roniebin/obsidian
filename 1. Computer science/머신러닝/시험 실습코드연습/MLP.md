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
 

  def forward(self, x):


  
```