---
{"dg-publish":true,"permalink":"/tp-3/lecture-notes/fri-17-10-25-variational-calculus/","tags":["gardenEntry"]}
---


# Variational Calculus 

Consider a function $S$
$$S = \int_{t_I}^{t_E} dt \space \mathcal L \left( q(t), \dot q (t), ... , t \right)$$
It is extrema iff $\delta S = 0 \iff \frac{dS}{d\epsilon}\Big|_{\epsilon =0} = 0$

so, for every small variation in argument / path  $$ q_\epsilon(t) = q(t) + \epsilon \cdot\delta q(t) \text{ and } \dot q_\epsilon(t) = \dot q + \epsilon \cdot \frac{d}{dt} \delta q(t) $$
we require that 
$$
\frac{dS[q_{\epsilon}]}{d \epsilon}\big|_{\epsilon=0} = 0
$$
i.e. 
$$
\delta S [q(t),\dot q(t)] = \underbrace{\frac{d}{d\epsilon}  \int_{t_I}^{t_E} dt \space\mathcal L(\vec q + \epsilon \cdot \delta q, \dot{\vec{q}} + \epsilon \frac{d}{dt} \delta q, t)}_{f(\epsilon;{q,\dot q, \delta q,\delta \dot q)}}
$$
For given $q,\dot q, \delta q,\delta \dot q$ we need
$$\frac{df(\epsilon)}{d \epsilon} = 0 $$
This Implies:
$$
\begin{aligned}
 0 = \delta S &= \frac{d}{d \epsilon} \int_{t_I}^{t_E} dt \space\mathcal L(q_\epsilon, \dot{\vec{q}}_\epsilon,...,t) \big|_{\epsilon=0}
 \\ &= \int_{t_I}^{t_E} dt \space  \frac{d\mathcal L}{dq_\epsilon}\frac{dq_\epsilon}{d\epsilon} +\frac{d\mathcal L}{d\dot q_\epsilon}\frac{d\dot q_\epsilon}{d\epsilon}\big|_{\epsilon=0} \\
 &=\int_{t_I}^{t_E} dt \space \partial_q \mathcal L \cdot \delta q + \frac{d}{dt} \delta q \cdot \partial_{\dot q} \mathcal L  \\
 &= \delta q \cdot \partial_{\dot q} \mathcal L  \big|_{t_I}^{t_E} + \int_{t_I}^{t_E} dt \space \partial_q \mathcal L\cdot \delta q \space - \frac{d}{dt} \delta q \cdot \partial_{\dot q} \mathcal L \\
 &=   \delta q \cdot \partial_{\dot q} \mathcal L  \big|_{t_I}^{t_E} + \int_{t_I}^{t_E} dt \cdot \delta q \space  \underbrace{\left( \space \partial_q \mathcal L  \space - \frac{d}{dt} \cdot \partial_{\dot q} \mathcal L  \right)}_\text{Euler-Lagrange Eqn}
 \end{aligned}$$
>[!note]- Example: Shortest Path on a cylinder 
>Initial Point:  $\vec q_I = z_I\cdot \hat z + R \cdot \hat r(\theta_I)$
>End Point: $\vec q_E = z_E \cdot \hat z + R \cdot \hat r(\theta_E)$
>
>The path length is given by $L = \int_{t_I}^{t_E} d \theta \space \left| \frac{d \vec q}{d \theta} \right|$
>
>Note: $\left|\frac{d \vec q}{d \theta} \right| = \left | \dot z(\theta)\cdot \hat z + R \cdot \hat \theta (\theta) \right|= \sqrt{\dot z^2+R^2}$
>
>so the path length becomes $$L = \int_{\theta_I}^{\theta_E} d\theta \space \sqrt{ (\dot z(\theta))^2 + R^2}$$
>The limits are fixed and the function depends only on z and its derivative this matches the setup for variational calculus 
>$$L = \int_{t_I}^{t_E} d\theta \space \mathcal L(z(\theta),\dot z(\theta))$$
>We must also fix the end and start points, making sure there is no variation of $\theta_I$ and $\theta_E$
> $$\rightarrow \delta L = 0 \text{ i.e. }\frac{dL}{d \epsilon} = 0\text{ with }\delta _Z (\theta _I) = \delta _z (\theta _E) = 0$$
> Finding the extrema: 
>  $$\begin{aligned}
>  0 &= \frac{d}{d\epsilon}\int_{t_I}^{t_E} d\theta \space \mathcal L(z(\theta),\dot z(\theta))\\
>  
>  \end{aligned}
>  $$
> We know that for this to be 0 the the Euler-Lagrange equation applies
> $$0 = \frac{\partial \mathcal L}{\partial z} = \frac{d}{d \theta} \frac{d \mathcal L}{d \dot z} = \frac{d}{d\theta} \space \underbrace{\frac{\dot z}{\sqrt{(\dot z(\theta))^2+ R^2}}}_{=\text{ k, const}}
> 
> $$
> (note: k is constant because z the derivative = 0)
> $$\begin{aligned}
>  k^2 = \frac{\dot z(\theta)}{\sqrt{R^2 + (\dot z(\theta))^2}} & \implies k^2 \cdot \left(\dot z(\theta))^2 + R^2 \right) = (\dot z(\theta)^2 \\
> & \implies \hat z(\theta) = \tilde k
> \end{aligned}$$
>Note: This gives us multiple solutions, we still need to verify we have the shortest
>![Fig1- Fri 17-10-25.jpg|300](/img/user/Fig1-%20Fri%2017-10-25.jpg) 


In TP1 we worked with conservative forces i.e. when F satisfied $F = - \nabla \Phi (\vec x, t)$
We can find newtons law by considering variations: 
$$\mathcal L = \frac{m}{2} \dot{\vec x^2} - \Phi(\vec x , t)$$
We introduce the **action** S
$$S = \int_{t_I}^{t_E} dt \space \mathcal L \left( \vec x, \dot{\vec x}, t \right)$$
We still need constant start and end points: $\delta \vec x(t_I) = \delta \vec x (t_E) = 0$
Then apply E-L eqn: (in the k-th direction)
$$-\frac{\partial \Phi}{\partial x_k} = \frac{\partial \mathcal L}{\partial x_k} = \frac{d}{dt} \frac{\partial \mathcal L}{\partial \dot x_k} = \frac{d}{dt} (m \dot x_k) = m \ddot{x_k}$$
$$\implies \underbrace{m \ddot x_k = - \nabla \Phi }_\text{Newtons 2nd Law!!} \qquad \iff \delta S = 0$$
>[!note]- Example: Mathematical Pendulum 
>
>$$\begin{aligned}
>\mathcal L & = \frac{m}{2}(x^2 + y^2) - mgy  - \Phi(R)\\
>\implies &m \ddot x  = -\partial_x \Phi(R)= -  \frac{\partial R}{\partial x} \cdot \dot \Phi(R) = -\frac{x}{R} \Phi'(R)\\
>&m\ddot y = -\partial y \Phi(R) = - \frac{y}{R} \Phi'(R)
>\end{aligned}$$
>With R = const.
>However this is hard to solve 

We will show the Euler-Lagrange equation does not care about coordinate changes

Choose $\vec x (\vec q, t)$ (any coordinate system)
$$\dot x_k = \sum_l \frac{\partial x_k}{\partial q_l} \cdot \dot q_l + \partial_t x_k$$
Note: 
$$
\frac{\partial \dot x_k}{\partial \dot q_m} = \frac{\partial x_k}{\partial q_m} \tag{1}
$$
So: 
$$
\begin{aligned}
\frac{d}{dt} \frac{\partial x_k}{\partial q_m} = \sum_l \frac{{\partial}^2 x_k}{\partial q_l q_m} \dot q_l + \frac{{\partial}^2 x_k}{\partial t \partial q_m} \\
= \frac{\partial}{\partial q_m}{}\sum_l \frac{\partial x_k}{\partial q_l} \dot q_l + \partial_t x_k
\end{aligned}
$$
Now we can apply E-L
$$
\begin{aligned}
\frac{d}{dt} \frac{\partial \mathcal L}{\partial \dot q_k} &= \frac{d}{dt} \sum_l \frac{\partial \mathcal L}{\partial \dot x_l} \underbrace{\frac{\partial \dot x_l}{\partial \dot q_k}}_{(1)} \\&= \frac{d}{dt} \sum_l \frac{\partial \mathcal L}{\partial \dot x_l} \frac{\partial x_l}{\partial q_k}\\
&= \sum_l \left[ \left( \frac{d}{dt} \frac{\partial \mathcal L}{\partial \dot x_l}\right) \frac{\partial x_l}{\partial q_k}+ \frac{\partial \mathcal L}{\partial \dot x_l} \cdot \left(  \frac{d}{dt} \frac{\partial x_l}{\partial q_k}\right) \right]\\
\text{Euler-Lagrange EQ} \implies&= \sum_l \left(\frac{\partial \mathcal L}{\partial x_l }\cdot \frac{\partial x_l}{\partial q_k} + \frac{\partial \mathcal L}{\partial \dot x_l} \frac{\partial \dot x_l}{\partial q_k}\right)\\
&= \frac{\partial \mathcal L}{\partial q_k} \text{(chain rule)}
\end{aligned}
$$
So we can solve the Pendulum with polar coordinates:

>[!note]- Example: Mathematical Pendulum 
>![WhatsApp Image 2025-10-18 at 23.26.47_de8fe4c1.jpg|100](/img/user/WhatsApp%20Image%202025-10-18%20at%2023.26.47_de8fe4c1.jpg)
>$$\begin{aligned} \mathcal L &= \frac{mR^2}{2} \dot{{\theta}}^2 + \frac{m{R}^2}{2} +mgR \cos \theta - \Phi (R) \\
>\frac{d}{dl}(mR^2 \dot \theta) &= 2m R \dot R \dot \theta + mR^2 \ddot \theta = -mgR \cdot \sin \theta \\
>m \ddot R &= \frac{d}{dt} \frac{\partial d \mathcal L}{\partial R} = \frac{\partial \mathcal L}{\partial R}= mg \cdot \cos \theta = \Phi '(R) + mR \dot \theta^2 \\
>\ddot \theta &= \frac{\theta}{R} \cdot \sin \theta \\
>\text{and } \\ \Phi '(R) &= -mg \cos \theta - mR \dot \theta^2
>\end{aligned}$$

