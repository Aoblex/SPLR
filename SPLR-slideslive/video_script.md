# Title Page
Hello, I’m Chenrui Wang from Shanghai University of Finance and Economics. Today I’ll present our work, The Sparse‑Plus‑Low‑Rank Quasi‑Newton Method for Entropic‑Regularized Optimal Transport. This is joint work with associate professor Yixuan Qiu. <|page|>

# The Problem
## The Primal Problem
We start with the entropic-regularized optimal transport problem.
Popularized by Cuturi, it incorporates an entropic regularization term into the OT problem. <|page|>

## The Dual Problem
One approach to solving it is to study its dual problem - maximizing the function L.
It is worth noting that we remove the redundant degree of freedom by setting beta_m to 0 globally, <|page|>

## The Main Objective
which leads to our final main objective f(x). It has some good properties: first, f(x) is strictly convex; second, the first and second order derivatives of f(x) have closed-form expressions.
Here, tilde means that the last column or element is removed. <|page|>

# The Sparse-Plus-Low-Rank Method
## Overview
Motivated by the sparse Hessian structure and other Hessian sparsification methods,
we introduce our Sparse-Plus-Low-Rank approach, which is based on a quasi-Newton framework.
The main idea of this method is to provide an accurate approximation of the Hessian matrix while maintaining its sparsity as much as possible.
We propose to approximate the Hessian by combining two components:
    A sparse part that retains only a small, carefully chosen subset of its entries.
    A low‑rank correction that captures the remaining information with just two vector terms.
This combination allows us to make accurate and efficient update steps without the cost of handling the full matrix. <|page|>

## Sparsification Scheme
In the sparsification stage, we first introduce the concept of 'Sparsification Scheme': the Hessian matrix is sparsified by sparsifying tilde T, which is the transport plan matrix T with the last column removed. <|page|>

## Sparsifying the Hessian Matrix
At each iteration, the sparsification consists of two parts:
    First, the elements in the first row and first column of tilde T are preserved, which serves as a sufficient condition for ensuring theoretical properties.
    Second, the largest one-hundred-rho percent elements of tilde T are preserved.
Finally, the selected elements in tilde T are the union of these two parts. <|page|>

## The Low-Rank Terms
In the low-rank stage, we draw inspiration from various quasi-Newton methods, especially the BFGS update rule.
We determine a, b, u, v by the secant equation.
Putting it together, the final approximated Hessian matrix is the sparse Hessian matrix plus the low-rank terms with an optional shift parameter. <|page|>

# Theorems
## Eigenvalue Structure
One of our key contributions is that we provide theoretical results to understand the
mechanism of Hessian sparsification.
Theorem 3 reveals how the eigenvalues of the Hessian matrix change during the sparsification process.
It guarantees the positive definiteness and a smaller condition number of the sparsified Hessian and also allows for a broad range of sparsification schemes. <|page|>

## Convergence Analysis
Moreover, we prove that the SPLR algorithm enjoys a global convergence property, and the convergence rate is at least linear. In practice, SPLR achieves super-linear-like convergence speed. <|page|>

# Results
## Settings
In the numerical experiments, we compare SPLR with 5 algorithms listed here. <|page|>

## Synthetic I
In synthetic one, the existing sparse Newton method SSNS represented by the dashed green line, is slow because the Hessian is relatively dense. <|page|>

## Synthetic II
In synthetic two, SSNS performs relatively well with a smaller density.
On the other hand, SPLR, represented by the solid blue line, performs well in both settings, showing its adaptivity to different OT settings. <|page|>

## MNIST and Fashion-MNIST
We then study the OT problem between a pair of images.
As is shown in the figure, first-order methods have a quite slow convergence speed, and the sparse Newton methods significantly accelerates the optimization, among which SPLR performs the best. <|page|>

## ImageNet
We reproduce the ImageNet experiment in the SSNS paper that uses OT to characterize the difference between two data distributions.
This experiment is interesting in that different values of eta have a large impact on the performance.
However, SPLR deals with this situation well via its low-rank term, making it perform consistently well on different eta values. <|page|>

## Ablation Study
Finally, we conduct an ablation study that compares SPLR with a purely sparsification-based method to verify that the low-rank term is indeed important.
It is clear from the plots that in all the settings, SPLR converges faster than its counterpart in dotted orange line, which highlights the benefits of the low-rank term. <|page|>

# Summary
In summary, our work:
    introduces a new way to speed up OT solvers by combining sparsification and low-rank correction
    develops new theoretical results to understand the mechanism of Hessian sparsification
    provides convergence guarantees for the SPLR method, and conducts extensive numerical experiments to demonstrate its performance <|page|>

and that's all for this presentation, thank you!