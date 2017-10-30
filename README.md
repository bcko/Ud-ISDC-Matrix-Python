# Ud-IntroSelfDrivingCars-MatrixClass

## Implementing a Matrix Class
In this project you will implement a Matrix class in Python. Specifically, you will implement the following methods:

```python
class Matrix:
  def determinant(self):
      # your code

  def trace(self):
      # your code

  def inverse(self):
      # your code

  def transpose(self):
     # your code

  # Overloaded operators

  def __add__(self,other):
    # your code

  def __sub__(self,other):
    # your code

  def __mul__(self,other):
    # your code
```

When your class is working properly you will be able to manipulate matrices in code as if they were regular numbers (for the most part). For example:

```python
> A = Matrix([ 
    [2,4], 
    [3,1] 
])
> print( A.transpose())
  2.0  3.0
  4.0  1.0
>
> I = Matrix([ 
    [1,0], 
    [0,1] 
])
>
> print(A*I)
  2.0  4.0
  3.0  1.0
>
> print(A * A.inverse())
  1.0  0.0
  0.0  1.0
```
