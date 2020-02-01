# desker
Calculate optimal layout of office space given constraints

This repository will consist of two components:
  1. A survey (using jupter notebook interactive sliders)
  2. An optimiser that uses the survey results and the constraints to calculate
     the optimum layout.


## The optimisation problem

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

### Specifying the objective function

Worker satisfaction is our objective function. We can determine the form of the
function by a survey to determine what each individual counts as their optimal
office layout, along with some strength of preference score against each of the
variables to signal how important that aspect of their choice is (a quadratic
voting component). The survey would need to constrain possible answers by the
constraints above.

 Perhaps the objective function would be something like:

<img src="https://latex.codecogs.com/gif.latex?f(v_{m})&space;=&space;\sum_{m=0}^{M}\sum_{n=0}^{N}{\sqrt{p_{n,m}}w_{n,m}}v_{m}" title="f(v_{m}) = \sum_{m=0}^{M}\sum_{n=0}^{N}{\sqrt{p_{n,m}}w_{n,m}}v_{m}" >

Where the `v_{m}` are our variables up to `M` total variables, and the `p_{n,m}`,
`w_{n,m}` are the worker preference strengths and variable values for each
worker (`n` from `0` to `N`) for each variable (`m`) obtained from the survey.

 We can then apply a optimisation method to optimise this function subject to
the constraints above.

### Specifying the constraints on the variables

For each desk there will be an associated capacity, budgetary cost and square-footage. The cost constraint will be something like:

<img src="https://latex.codecogs.com/gif.latex?C&space;=&space;\sum_{m=0}^{M}{c_{m}v_{m}}" title="C = \sum_{m=0}^{M}{c_{m}v_{m}}" >

Similarly for the space constraint:

<img src="https://latex.codecogs.com/gif.latex?S&space;=&space;\sum_{m=0}^{M}{s_{m}v_{m}}" title="S = \sum_{m=0}^{M}{s_{m}v_{m}}" >

And for the population constraint:

<img src="https://latex.codecogs.com/gif.latex?Q&space;=&space;\sum_{m=0}^{M}{q_{m}v_{m}}" title="Q = \sum_{m=0}^{M}{q_{m}v_{m}}" >

I need someone who makes the decisions to specify all of these `c's` and `s's`
to constrain the problem. I suspect we might need to underweight the occupancy
value of meeting spaces, because most meetings do not use all the chairs in the
meeting space.

## The survey

The survey will be subject to the same constraints to specify the problem so
that each individual can perform their own personal optimisation! There does
need to be one additional constraint in the survey, and that is to limit the
total preference credits used to 100.

