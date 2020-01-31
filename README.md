# desker
Calculate optimal layout of office space given constraints


This is a simple optimisation problem. Given a set of constraints, e.g on:
   * cost
   * space
   * number of workers
and a set of variables, e.g:
   * number of quiet desks
   * number of medium-quiet desks
   * number of meeting areas (formal)
   * number of meeting areas (informal)
Maximise worker satisfaction.

Worker satisfaction is our objective function. We can determine the form of the
function by a survey to determine what each individual counts as their optimal
office layout, along with some strength of preference score against each of the
variables to signal how important that aspect of their choice is (a quadratic
voting component). The survey would need to constrain possible answers by the
constraints above.

 Perhaps the objective function would be something like:

#href="https://www.codecogs.com/eqnedit.php?latex=f(v_{m})&space;=&space;\sum_{m=0}^{M}\sum_{n=0}^{N}{p_{n}^{2}w_{n}}v_{m}"  
<img src="https://latex.codecogs.com/gif.latex?f(v_{m})&space;=&space;\sum_{m=0}^{M}\sum_{n=0}^{N}{p_{n}^{2}w_{n}}v_{m}" title="f(v_{m}) = \sum_{m=0}^{M}\sum_{n=0}^{N}{p_{n}^{2}w_{n}}v_{m}" >

Where the `v_{m}` are our variables up to `m` variables, and the `p_{n,m}`,
`w_{n,m}` are the worker preference strengths and variable values for each
worker (`n`) for each variable (`m`).

 We can then apply a optimisation method to optimise this function subject to
the constraints above.

