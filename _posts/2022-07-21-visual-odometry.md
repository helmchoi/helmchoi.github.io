---
layout: post
title:  Study on vision (ongoing)
categories: Notes
use_math: True
---

## Fundamentals on Epipolar Geometry

### 1. Fundamental Matrix $F$
$$x'=P'X, x=PX$$
$X=P^+ x + \lambda C$, where $PC=0$
$$l'=[e']_\times x'=[P'C]_\times (P'P^+ x)=[e']_\times PP'x=Fx$$
Since $x'^T l'=0$, $x'^TFx=0$.

If $P=K[I|0], P'=K'[R|t]$, $P^+ =[K^{-1}; 0^T], C=[0;1]$
\begin{align}
F&=[P'C]_\times P'P^+\\
&=[K't]_\times K'RK^{-1}\\
&=K'^{-T}[t]_\times RK^{-1}\\
&=K'^{-T}R[R^T t]_\times K^{-1}\\
\end{align}

### 2. Essential Matrix $E$


## Visual Odometry


## Sensor Fusion
### 1. Loosely coupled vs. Tightly coupled
