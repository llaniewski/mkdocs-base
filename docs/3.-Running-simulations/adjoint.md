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

- **Objective function** -- let's call it \(J\)
- The set of **design parameters** (together with bonds on them) -- let's call them \(\alpha\)

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

The need for Adjoint calculation have to be declared in the xml configuration of the computation case. As we mentioned earlier, adjoint is a method of propagation of sensitivity, so we need first to define the objective function. In TCLB we declare the objective as a combination of Globals. For each Global (e.g. Flux) we have a Setting (e.g. FluxInObj), which controls what is the weight of said Global (e.g. Flux) in the overall objective. For instance we can set:

```xml
<Params FluxInObj="1.0"/> <Params HeatInObj="-2.0"/>
```

this will mean that: `Objective=Flux-2*Heat`. When we have a objective defined we can run the adjoint calculation.

## Steady Adjoint

Steady Adjoint calculation is a process of iterating the adjoint fixed point problem. You can request it with:
```xml
<Adjoint Iterations="1000" type="steady"/>
```
This should be done only after converging the primal problem. Otherwise the results would not be representative.

### One-shot Optimization

For steady adjoint we can run an additional type of calculation. It is what sometimes is called *one-shot* optimization. Each run of this approach make one iteration of primal solution, one iteration of the adjoint, and one iteration of a simple optimization algorithm. This allows for simultanious convergence of Primal and Adjoint problems, and optimization. *This is implemented only for topology optimization.* The optimization algorithm is the simplest steepest descent approach, moving the parameters in the direction of the gradient by a specific small coeficient. In each iteration parameters \(\alpha\) is moved by \(\zeta\nabla_\alpha J\), where \(\zeta\) (`Descent`) is the speed of change. The one-shot optimization can be run with:

```xml
<Params Descent="0.1"/>
<OptSolve Iterations="1000"/>
```

## Unsteady Adjoint

```xml
<Adjoint type="unsteady" NumberOfSnaps="14">
  <Solve Iterations="1000"/>
</Adjoint>
```

# Defining parameters

## Field Parameter

```xml
<FieldParameter field="w" where="DesignSpace"/>
```

## Optimal Control

```xml
<OptimalControl what="MovingWallVelocity-DefaultZone" lower="-0.1" upper="0.1"/>
```

### Reducing the dimensionality of the parameter space

```xml
<BSpline order="4" nodes="10">
   <OptimalControl what="MovingWallVelocity-DefaultZone" lower="-0.1" upper="0.1"/>
</BSpline>
```

# Optimization

```xml
<Optimize method="MMA" MaxEvaluations="10">
  <Adjoint type="unsteady">
    <Solve Iterations="1000"/>
  </Adjoint>
</Optimize>
```

