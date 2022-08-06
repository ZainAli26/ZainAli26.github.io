# Linear Regression

### What is Regression in Statistics?
Regression is the statistical approach of predicting the outcome scalar value based on the given one or more scalar variables on which the outcome is dependent.

### What is Linear Regression?

Linear regression is the linear approach of modeling the realtionship between the o ne or more scalar variables to the predicted scalar value.

### Linear Regression Approach

Linear regression is based on this simple equation. The above equation is just a simple linear function to predict the outcome `y` based on dependent variable `x`.
```
h(x) = a * x + b = y
```
where `h(x)` is the hypothesis function, `y` means the predicted scalar outcome and `x` is the input scalar variable. The `a` and `b` are the parameters which are responsible for drawing a right relationship between dependent outcome and input variable. Here we will further discuss how can we optimize these parameters to have the right relationship and expected outcome.

#### Optimizing the Algorithm

We need to optimize the values of parameters `a` and `b` to figure out the best possible value of `h(x)`. As linear regression is a supervised learning algorithm whhich means that we will do all these optimization based on some training data.

- The first step in the optimization is to figure out the cost function of the algorithm which in case of linear regression will be
```
cost Function = 1/2mΣ(h(x) - y)^2,
J(a, b) = 1/2mΣ(h(x) - y)^2,
```
- In the next step we will try to figure out how to minimize tcost function. We need to figure out the values of `a` & `b` which minimizes this cost function. We wil do this using the grdient descent algorithm.
Initially we will take random values for both `a` and `b` 
```
a := a - α * ∂/∂a(J(a,b))
b := b - α * ∂/∂b(J(a,b))
Reapeat the above step until we figured out the values which gives us the minimal value for cost function.
```

In the above equation we are finding the partial derivative of the cost function based on `a` and `b` in respective equation and then updating the value of the parameters. 
`α` is the hypermeter which decides how much we want ot change the values of parameters n one iteration. If value of `α` is very small it will take edges to reach the optimal point, on the contray if it is too big it will keep on taking big jumps and might never reach the optimal point, so having this value optimal is really important to choose the right value for this parameter.

`∂/∂a(J(a,b))` and `∂/∂b(J(a,b))` are the partial derviatives of the cost function based on the parameters `a` and `b` respectively.

- In this step we will find out the partial derivatives to parameters `a` & `b`.

For `a`
```
∂/∂a(J(a,b)) = ∂/∂a(1/2mΣ(h(x) - y)^2)
∂/∂a(J(a,b)) = 1/mΣ(h(x) - y) * ∂/∂a(h(x) - y)
∂/∂a(J(a,b)) = 1/mΣ(h(x) - y) * ∂/∂a(a * x + b - y)
∂/∂a(J(a,b)) = 1/mΣ(h(x) - y) * (x + 0 - 0)
∂/∂a(J(a,b)) = 1/mΣ(h(x) - y) * x
```

For `b`
```
∂/∂b(J(a,b)) = ∂/∂b(1/2mΣ(h(x) - y)^2)
∂/∂b(J(a,b)) = 1/mΣ(h(x) - y) * ∂/∂b(h(x) - y)
∂/∂b(J(a,b)) = 1/mΣ(h(x) - y) * ∂/∂b( * x + b - y)
∂/∂b(J(a,b)) = 1/mΣ(h(x) - y) * (0 + 1 - 0)
∂/∂b(J(a,b)) = 1/mΣ(h(x) - y)
```

So the equation to update the parameters will be something like that
```
a := a - α * ∂/∂a(1/mΣ(h(x) - y) * x)
b := b - α * ∂/∂b(1/mΣ(h(x) - y))
```

After few iteration we will see that our cost function is getting minimized and we are reachin our goal. There will be a point when it will converge and we won't see any improvements further that will be a point we will stop further iteration and will ask our model to predict the outcomes.