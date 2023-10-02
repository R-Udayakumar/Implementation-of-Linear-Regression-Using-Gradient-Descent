# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import required libraries in python for Gradient Design.
2. Upload the dataset and check any null value using .isnull() function.
3. Declare the default values for linear regression.
4. Calculate the loss usinng Mean Square Error.
5. Predict the value of y.
6. Plot the graph respect to hours and scores using scatter plot function.

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Udayakumar R
RegisterNumber:  212222230163
*/
```
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data = pd.read_csv("ex1.txt",header = None)

plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Popluation of City (10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def computeCost(x,y,theta):
  m = len(y)
  h = x.dot(theta)
  square_err = (h - y)**2
  return 1/(2*m) * np.sum(square_err)

data_n = data.values
m = data_n[:,0].size
x = np.append(np.ones((m,1)), data_n[:,0].reshape(m,1),axis=1)
y = data_n[:,1].reshape(m,1)
theta = np.zeros((2,1))

computeCost(x,y,theta)

def gradientDescent (x,y,theta,alpha,num_iters):
  m = len(y)
  J_history = []

  for i in range (num_iters):
    predictions = x.dot(theta)
    error = np.dot(x.transpose(),(predictions -y))
    descent = alpha *1/m*error
    theta -= descent
    J_history.append(computeCost (x,y,theta))

  return theta, J_history

theta, J_history = gradientDescent(x,y,theta,0.01,1500)
print("h(x) = " +str(round(theta[0,0],2))+ " + " +str(round(theta[1,0],2)) +"x1")

plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Gradient Descent")

plt.scatter(data[0],data[1])
x_value = [x for x in range(25)]
y_value = [y*theta[1] + theta[0] for y in x_value]
plt.plot(x_value, y_value, color = "r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,00s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def predict(x,theta):
  predictions = np.dot(theta.transpose(), x)
  return predictions[0]

predict1 = predict(np.array([1,3.5]),theta)*10000
print("For population = 35,000, We predict a profit of $ "+str(round(predict1,0)))

predict2 = predict(np.array([1,7]),theta)*1000
print("For population = 70,000, We predict a profit of $ "+str(round(predict2,0)))

```

## Output:
## PROFIT PREDICTION GRAPH
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/be55b87e-ffa6-40ca-b8fb-564fa6f62fe5)
## COMPUTE COST VALUE
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/789dce27-537a-41c1-8901-9b648d394caa)
## h(x) VALUE
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/d0b61a83-6adb-4631-8ff5-46f54eb0a6d2)
## COST FUNCTION USING GRADIENT DESCENT GRAPH
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/23388354-3659-4423-887e-1e66e71093f2)
## PROFIT PREDICTION GRAPH
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/d4b62421-a752-462a-9ce5-3cf0d16acba5)
## PROFIT FOR POPULATION 35,000
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/f30f778d-1830-4793-a713-233025f98cc5)
## PROFIT FOR POPULATION 70,000
![image](https://github.com/R-Udayakumar/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118708024/7d208011-7dfd-4fb3-a7b4-2ec4d751a6ae)



## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
