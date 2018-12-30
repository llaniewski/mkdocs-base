---
title: Adjoint
author: "Łukasz Łaniewski-Wołłk"
date: "2018"
---

# Adjoint

Generaly Adjoint is a method for propagation of sensitivities from a selected objective
function throughout the code (backwards) until the design parameters. This allows for an
efficient calculation of the sensitivity (gradient) of the objective with respect to
any number of parameters or variables.

It is very hard to achieve, as it is a highly intrusive method (the numerical code have to
be specially designed to allow for it), andeven harder to make efficient. The TCLB code
introduced Adjoint into the source code quite early on, allowing for a well parallelized
and fast adjoint implementation, but making some parts of the code quite cumbersome.

The main gain of the code begin able to perform adjoint calculation is the gradient
information. Such information can be used for gradient-based optimization algorithms.
Such algorithms perform much better in the cases with a high number of parameters
(which is the case both in Topology Optimization, and Open Loop Optimal Control).

In any gradient-based optimization done with an Adjoint code, there are three things to separate:

- **Primal** - The primal problem to solve (in our case it can be CFD done with LBM)
- **Adjoint** - The adjoint problem, which calculates the sensitivities of the objective to all variables in the code (including the design parameters)
- **Optimziation Algorithm** - The algorithm which takes the gradient information and uses it to change the desing variables to achieve the best value of the objective function.

For the second end third thing to work, we need two things to be defined:

- **Objective function**
- The set of **design parameters** (together with bonds on them)

To understand the mechanisms of sensitivity propagation in TCLB, we can divide adjoint
computations into two types: **steady** and **unsteady**. If the Primal problem has a stationary
solution \(x\), this means that \(x\) is a solution to a fixed point iteration \(x=f(x)\).
This in turn means that the Adjoint problem can be similarly formulated as a fixed point
problem. This makes solving it much simpler, and allows us to iterate it in a simple way.
On the other hand we have usteady Primal problems. By them we mean solutions in which the
time evolution of e.g. the flow is important, not the *final* (converged) solution. In
such case adjoint has to propagate the sensitivities throughout the whole iterative process
starting at the end of the primal simulation, and going backwards. It's easy to notice that
the latter type of adjoint is much more computationally challenging.

# Setting up Adjoint Calculations

## Steady Adjoint

```xml
<Adjoint Iterations="1000" type="steady"/>
```

### One-shot Optimization

```xml
<Params Descent="0.1"/>
<OptSolve Iterations="1000"/>
```

## Unsteady Adjoint

```xml
<Adjoint type="unsteady">
  <Solve Iterations="1000"/>
</Adjoint>
```

# Defining parameters

## Field Parameter

```xml
<FieldParameter/>
```

## Optimal Control

```xml
<OptimalControl/>
```

# Optimization

```xml
<Optimize method="MMA" MaxEvaluations="10">
  <Adjoint type="unsteady">
    <Solve Iterations="1000"/>
  </Adjoint>
</Optimize>
```

