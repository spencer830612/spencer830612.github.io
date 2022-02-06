 1217
# Surface Parametrization
## Torus

Use Local chart. It  can be computed by the least squares conformal map.

### Global parametrization of Torus
![](https://i.imgur.com/MvOkjxi.png)
![](https://i.imgur.com/YL7Oz7O.png)

simplex:
Given a set of affining independent points(不共面，共線等等) $$\{v_0,\cdots,v_k\}\subset\mathbb{R},\, d\geq k+1$$, The k-simplex $$\sigma$$ is the __minimal convex set__ (convex hull) containing $$v_0,...,v_k$$, denoted as $$\sigma=[v_0,\cdots,v_k]=\left\{\sum^k_{l=1}\alpha_l v_l| \alpha_l\geq0, \sum^k_{l=1}\alpha_l=1\right\}$$

IN particular,
* a point $v_0$ is a 0-simplex
* an interval $[v_0,v_1]$ is a 1-simplex.
* a triangle $[v_0,v_1,v_2]$ is a 2-simplex.
* a tetrahedron $[v_0,v_1,v_2,v_3]$ is  a 3-simplex.

以上的東西不會往下退化一個維度。

### Facet
The set of facets of $[v_0,\cdots,v_k]$ is facet$([v_0,\cdots,v_k])=\left\{[v_0,\cdots,\hat{v_l},\cdots,v_k]\right\}^k_{l=0}$.
The notion $\hat{\cdot}$ is denoted by omitting it.

e.g.
facet$([v_0,v_1,v_2])=\{[v_1,v_2],[v_0,v_2],[v_0,v_2]\}$
![](https://i.imgur.com/OfD7WTG.png)

### Simplicial Complex
A simplicial complex $\Sigma$ is a set of simplices satisfies:
* If $\sigma\in\Sigma$, then facet$(\sigma)\subset\Sigma$.
* If $\sigma_1,\,\sigma_2\in\Sigma$, and $\sigma_1\cap\sigma_2\not=\phi$. then $\{\sigma_1\cap\sigma_2\}=\text{facet}(\sigma_1)\cap\text{facet}(\sigma_2)$.

### Underlying Space
The underlying space of $\Sigma$ is $|\Sigma|=\bigcup_{\sigma\in\Sigma}\sigma$

### Triangular Mesh
A triangular mesh $M=|\Sigma|\subset\mathbb{R}^3$ is the underlying space of a homogenuous simplicial 2-complex $\Sigma=\mathcal{V}\cup\mathcal{E}\cup\mathcal{F}$ composed of 
* vertices $\mathcal{V}=\{v_1,\cdots,v_n\}\subset\mathbb{R}^3$
* Faces $\mathcal{F}=\{[v_i,v_j,v_l]\}$
* Edges $\mathcal{E}=\left\{[v_i,v_j]\,\left|\,[v_i,v_j,v_k]\in\mathcal{F}\text{ for some } v_k\in\mathcal{V}\right.\right\}$
![](https://i.imgur.com/XdZ3nDK.png)

### Chain group
A k-chain on $\Sigma$ is a linear conbination of k-simplex $\Sigma\lambda_l\sigma_l,\,\lambda_l\in\mathbb{Z}$ (Consider the group operation)
The set of k-chain forms an abelian group $C_k(\Sigma)=\left\{\sum_l\lambda_l\sigma_l\,|\,\lambda_l\in\mathbb{Z}\right\}$ with $+:C_k(\Sigma)\times C_k(\Sigma)\to C_k(\Sigma)$ defined as $\sum_l\alpha_l\sigma_l+\sum_l\beta_l\sigma_l=\sum_l(\alpha_l+\beta_l)\sigma_l$.
![](https://i.imgur.com/xF3cmOM.png)

### Boundary operator
The boundaryoperator on k-chains is a homomorphism $\partial z_k:C_k(\Sigma)\to C_{k-1}(\Sigma)$ defined as $\partial_k[v_0,\cdots,v_k]=\sum^k_{l=0}(-1)^l[v_0,\cdots,\hat{v_l},\cdots,v_k]$. In particular, $\partial_0v_0=0$, and
* $\partial_1([v_0,v_1])=v_1-v_0$.
* $\partial_2([v_0,v_1,v_2])=[v_1,v_2]-[v_0,v_2]+[v_0,v_1]$.

#### Prop: The boundary of boundary is empty.
That is: $\partial_{k-1}\circ\partial_k=0$.
In particular, $\partial_1\circ\partial_2[v_0,v_1,v_2]=\partial_1([v_1,v_2]-[v_0,v_3]+[v_1,v_2])$
$=\partial_1[v_1,v_2]-\partial_1[v_0,v_3]+\partial_1[v_1,v_2]$
$=(v_2-v_1)-(v_2-v_0)+(v_1-v_0)-0$

蒐集這些 close chain, 也會成一個群。

### Closed Chain Group
For each $k\geq 0$, the subgroup $\ker\partial_k\subseteq C_k(\Sigma)$ is defined as $Z_k(\Sigma)=\{\sigma\in C_k(\Sigma)\,|\,\partial_k\sigma=0\}$
Each elements in $Z_k(\Sigma)$ is called a closed k-chain.
e.g. $\partial_1([v_0,v_1]+[v_1,v_2]+[v_2,v_3]+[v_3,v_0])=0$![](https://i.imgur.com/73tgLNC.png)
#### Boundary Chain group
![](https://i.imgur.com/MPLbWlg.png)

For each $k\geq0$, the subgroup $\text{Im }\partial_{k+1}\subseteq C_k(\Sigma)$ is defined as $B_k(\Sigma)=\{\sigma\in C_k(\Sigma)\, | \, \sigma=\partial_{k+1}r\text{ for some }r\in C_{k+1}(\Sigma)\}$
Each elements in$B_l(\Sigma)$ is calld an exact k-chain.

#### Prop: Exact chains are closed. That is, for each $k\geq0$, $B_k(\Sigma)\subseteq Z_k(\Sigma)$.
proof: Given $\sigma\in B_k(\Sigma)$.Then $\sigma=\partial_{k+1}r$ for some $r\in C_{k+1}(\Sigma)$. Hence$\partial_k\sigma=\partial_{k}\circ\partial_{k+1}r=0$. Therefore, $\sigma\in\ker\partial_k=Z_k(\Sigma)$

### Simplicial Homology Group
The quotient group $H_k(\Sigma)=Z_k(\Sigma)/B_k(\Sigma)$ is called the k-dimensional homology group.
Each element $[z_k]\in H_k(\Sigma)$ is called k-dimensional homologous group.
![](https://i.imgur.com/gU7ALcY.png)

Two k-chains $z^1_k$ and $z^2_k$ are homologous if $z^1_k-z^2_k=\partial_{k+1}Z_{k+1}$ for some $z_{k+1}\in C_{k+1}(\Sigma)$

### Cut Graph Algorithm
* Input: a triangular Mesh M.
* Output: a cut graph G.

Steps:
1. Compute the dual mesh $M^*$
把面變成點，點變成面
![](https://i.imgur.com/9HxwSRU.png)
2. Compute a minimal spanning tree $T^*$ of $M^*$
3. Let $G=\{e\in M\,|\,e^*\not\in T^*\}$
5. While exist $v\in G$ with $\text{deg }(v)=1$, remove $v$ and $[v,w]\,\forall w\in G$, end.
6. Return $G$. 

### Algorithm: Homology Group Basus
* Input: $M=|\Sigma|$
* Output: A basis for $H_1(\Sigma)$

Steps:
1. Compute a cut graph $G$ of $M$.
2. Compute a minimal spanning tree $T$ of $G$.
3. Let $G-T=\{e_1,\cdots,e_{2g}\}$
4. For $l=1,\cdots,2g$, find the unique loop $r_l$ in $T\cup\{e_l\}$, end.
5. Return $H_1(\Sigma)=\{r_1,\cdots,r_{2g}\}$

### Cochain Group
A k-cochain on $\Sigma$ is a functional $\sigma^k:C_k(\Sigma)\to\mathbb{Z}$. The collection set of all k-cochain forms a abelian group $C^k(\Sigma)=\{\sigma^k:C_k(\Sigma)\to\mathbb{Z}\}$ with $+:C^k(\Sigma)\times C^k(\Sigma)\to C^k(\Sigma)$ defined as $(\sigma^k_1+\sigma^k_2)(r)=\sigma^k_1(r)+\sigma^k_2(r)$. The cochain $\sigma^k$ is a homomorphism between $C_k(\Sigma)$ and $\mathbb{Z}$.

### Coboundary Operator
The coboundary operator $\delta^k:C^k(\Sigma)\to C^{k+1}(\Sigma)$ is the dual of the boundary operator $\partial_{k+1}:C_{k+1}(\Sigma)\to C_k(\Sigma)$ defoned as $\delta^k\sigma^k(r_{k+1})=\sigma^k(\partial_{k+1}r_{k+1})$

e.g.: the coboundary of a 1-cochain $\sigma^1:C_1(\Sigma) \to \mathbb{Z}$ is a 2-cochain $\delta^1\sigma^1:C_2(\Sigma)\to\mathbb{Z}$ given by $\delta^1\sigma^1([v_0,v_1,v_2])=\sigma^1(\partial_2[v_0,v_1,v_2])$.

$\sigma^1(\partial_2[v_0,v_1,v_2])=\sigma^1([v_0,v_1])+\sigma^1([v_1,v_2])-\sigma^1([v_0,v_2])$

#### Prop: Suppose $\sigma^k\in C^k(\Sigma)$ and $r\in C_{k+2}(\Sigma)$, then $\delta^{k+1}(\delta^k \sigma^k)(r)=\delta^k\sigma^k(\partial_{k+2}r)=\sigma^k(\partial_{k+1}\circ\partial_{k+2}r)=\sigma^k(o)=0$

Hence $\delta^{k+1}\circ\delta^k=0$.

### Closed Cochain group
For each $k\geq 0$,the subgroup $\ker\delta^k\subseteq C^k(\Sigma)$ is defined as $Z^k(\Sigma)=\{\sigma\in C^k(\Sigma)\,|\,\delta^k\sigma=0\}$. Each element is called a closed k-cochain.

### Boundary cochain group
For each $k\geq0$, the subgroup $\text{Im }\delta^{k-1}\subseteq C^k(\Sigma)$ is denoted as $B^k(\Sigma)=\{\sigma\in C^k(\Sigma)\, |\, \sigma=\delta^{k-1}r\text{ for some }r\in C^{k-1}(\Sigma)\}$. Each element in $B^k(\Sigma)$ is called an exact k-cochain.

### Cohomology group
The quotient group $H^k(\Sigma)=Z^k(\Sigma)/B^k(\Sigma)$ is called the k-dimentional cohomology group.

1224

## Completion of Cohomology Group Basis
![](https://i.imgur.com/BvPxxWg.png)

Construct $M_k$, $k=1,\,2\,\cdots\,$, with $\partial M_k=r^+_k-r^-_k$. For each $k$, define a function
$f_k:M_k\to \mathbb{R}$ by
$f_k|_{M_k-\partial M_k}=0,f_k|_{r^-}=0,\,f_k|_{r^+}=1$
A cohomology group basis is the st of 1-form $\omega_k=\mathcal{E}(M)\to\mathbb{R}$ guven as $\omega_k([v_i,v_j])=f(v_j)-f(v_i)$, $k=1,2,\cdots,2g$

## Harmonic 1-form Basis

Given a closed 1-form $\omega$. There is a **unique** exact 1-form such that $\omega+df$ is a harmonic 1-form cohomologous to $\omega$, which can be obtained by solving the linear system
$\sum_{v_j\in N(v_j)}\frac{\cot\theta_{i,j}+\cot\theta_{j,i}}{2}(\omega([v_i,v_j])+f(v_j)-f(v_j))=0$ for $v_i\in\mathcal{V}(M)$, $f$ is unknowned, and $\omega$ is given.

But the rank of Matrix of the Laplacian is $n-1$, therefore $f$ is not unique.

What is 1-form? We can see it as a :
![](https://i.imgur.com/RyOApsY.png)

### Harmonic function
Set $f(v_k)=0$. Define $f(v_l)=\int_{\gamma(v_k,v_l)}\omega$, where $\gamma(v_k,v_l)$ is the path from $v_k$ to $v_l$.

### Hodge Conjugate
The 1-form $\omega:H(M)\to\mathbb{R}$ is associated with a vector field $\mathbf{w}$ such that $\omega(\mathbf{v})=\left<\mathbf{w},\mathbf{v}\right>$ for every $\mathbf{v}=v_j-v_i$ with $[v_i,v_j]\in H(M)$.
The vector field $\mathbf{w}$ is known as the vector-valued 2-form $\mathbf{w}:\mathcal{F}\to\mathbb{R}^3$ satisfies
$\left<\mathbf{w}([v_i,v_j,v_k]),v_j-v_i\right>=\omega([v_i,v_j])$, $\left<\mathbf{w}([v_i,v_j,v_k]),v_k-v_j\right>=\omega([v_j,v_k])$, $\left<\mathbf{w}([v_i,v_j,v_k]),v_i-v_k\right>=\omega([v_k,v_i])$.
As a result, $\mathbf{w}$ can be explicitly formulated as $\mathbf{w}([v_i,v_j,v_k])=\frac{1}{2\left|[v_i,v_j,v_k]\right|}\left(\omega([v_i,v_j])v_k+\omega([v_k,v_i])v_j+\omega([v_j,v_k])v_i\right)\times\mathbf{n}([v_i,v_j,v_k])$.

Then, the hodge conjugate of $\mathbf{w}$ is given as $*\mathbf{w}=\mathbf{n}\times\mathbf{w}$.

The holomorphic 1-form is given by $z=\omega+i*\omega$, where $*\omega$ is the Hodge conjugate of $\omega$.

### Holomorphic 1-Form Basis
Given a harmonic 1-form basis $\beta=\{\omega_1,\omega_2,\ldots,\omega_{2g}\}$. Then $*\omega$ can be formulated as $*\omega=\sum^{2g}_{k=1}\mu_k\omega_k$. The unknown coefficients $\{\mu_k\}_{k=1}^{2g}$ satisfy $\int_M\omega_j\wedge*\omega=\sum^{2g}_{k=1}\mu_k\int_M\omega_j\wedge\omega_k$, for $j=1,\ldots,2g$.
Where $\left(\omega_k\wedge*\omega\right)(\tau)=\mathbf{w}_k(\tau)\times*\mathbf{w}(\tau)\cdot\mathbf{n}(\tau)|\tau|$.
As a result, $\int_M\omega_j\wedge*\omega=\sum_{\tau\in\mathcal{F}(M)}(\omega_k\wedge*\omega)(\tau)=\sum_{\tau\in\mathcal{F}(M)}\mathbf{w}_k(\tau)\times*\mathbf{w}(\tau)\cdot\mathbf{n}(\tau)|\tau|$.

Therefore, $\{\mu_k\}^{2g}_{k=1}$ can be computed by the linear system
$\begin{bmatrix}
\int_M\omega_1\wedge\omega_1&\int_M\omega_1\wedge\omega_2&\cdots&\int_M\omega_1\wedge\omega_{2g}\\
\int_M\omega_2\wedge\omega_1&\int_M\omega_2\wedge\omega_2&\cdots&\int_M\omega_2\wedge\omega_n\\
\vdots&\vdots&\cdots&\vdots\\
\int_M\omega_{2g}\wedge\omega_1&\int_M\omega_{2g}\wedge\omega_2&\cdots&\int_M\omega_{2g}\wedge\omega_{2g}
\end{bmatrix}\begin{bmatrix}
\mu_1\\
\mu_2\\
\vdots\\
\mu_{2g}
\end{bmatrix}=\begin{bmatrix}
\int_M\omega_1\wedge*\omega\\
\int_M\omega_2\wedge*\omega\\
\vdots\\
\int_M\omega_{2g}\wedge*\omega
\end{bmatrix}$

Ultimately, a basis for holomorphic 1-form is given as $\{z_k=\omega_k+i*\omega_k\}^{2g}_{k=1}$
