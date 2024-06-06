202405311618

Status: #idea

Tags: [[introspection]]

# General Notation

$\mathcal{F}(\cdot)$: Perception function
$\boldsymbol{\hat{x}}_t^{\mathcal{F}}$: The estimates of $\mathcal{F}$ at time $t$
$\boldsymbol{\hat{y}}_t^{\mathcal{F}}$: The estimates of states at time t and required by $\mathcal{F}(\cdot)$
$\boldsymbol{z}_t^{\mathcal{F}}$: Observations at $t$ processed by $\mathcal{F}(\cdot)$
$\phi^{\mathcal{F}}$: PDF of the error distribution of the output of $\mathcal{F}(\cdot)$

$\boldsymbol{\hat{x}}_t^{\mathcal{F}} = \boldsymbol{x}^F_t + \delta\boldsymbol{x}^F_t$, $\delta\boldsymbol{x}^F_t \sim \phi^{\mathcal{F}}(\boldsymbol{z}_t^{\mathcal{F}}, y^F_{t-1})$
$\hat{\phi}^{\mathcal{F}}=\mathbb{I}(\mathcal{F}[\boldsymbol{z}_t^{\mathcal{F}},\boldsymbol{\hat{y}}_t^{\mathcal{F}}])$, not all perception functions necessarily include the intermediate state factors $\boldsymbol{\hat{y}}_t^{\mathcal{F}}$

## Example

$\mathcal{F}(\cdot)$: It can be a human tracking algorithm
$\boldsymbol{\hat{x}}_t^{\mathcal{F}}$: 3D pose of pedestrians
$\boldsymbol{\hat{y}}_t^{\mathcal{F}}$: Bounding boxes of pedestrians
$\boldsymbol{z}_t^{\mathcal{F}}$: Image
$\phi^{\mathcal{F}}$: PDF of the error distribution of the output of $\mathcal{F}(\cdot)$

## IV-SLAM (ORB-SLAM with introspection)

SLAM has two modules or functions. The feature extraction or frontend ($\mathcal{F}_{\text{SF}}$) and the pose estimation of backend ($\mathcal{F}_{\text{SB}}$).

### Frontend

$$\begin{equation}
\boldsymbol{\hat{x}}_t^{\mathcal{F}_{\text{SF}}} =\ 
\mathcal{F}_{\text{SF}}(\
\boldsymbol{z}_t^{\mathcal{F}_{\text{SF}}}, \ 
\boldsymbol{\hat{x}}_{t-1}^{\mathcal{F}_{\text{SF}}} \
)
\end{equation}$$
$\boldsymbol{\hat{x}}_t^{\mathcal{F}_{\text{SF}}}:$ extracted and matched image features at time $t$. ${\hat{\boldsymbol{x}}}_{t}^{{\mathcal{F}}_{\mathrm{SF}}}=\left\{{\hat{\boldsymbol{x}}}_{t,k}^{{\mathcal{F}}_{\mathrm{SF}}}|{\hat{\boldsymbol{x}}}_{t,k}^{{\mathcal{F}}_{\mathrm{SF}}}\in\mathbb{R}^{2},k\in[1,N]\right\}$
$\boldsymbol{z}_t^{\mathcal{F}_{\text{SF}}}:$ input images.

### Backend

$\boldsymbol{M}\,=\,\left\{\boldsymbol{p}_{k}^{W}|\boldsymbol{p}_{k}^{W}\in\mathbb{R}^{3},k{\in}[1,N]\right\}$, the map
$\boldsymbol{T}^{\text{W}}$: pose of the camera

$$\begin{equation}
\boldsymbol{\hat{x}}_t^{\mathcal{F}_{\text{SB}}} =\ 
\mathcal{F}_{\text{SB}}(\
\boldsymbol{z}_t^{\mathcal{F}_{\text{SB}}}, \ 
\boldsymbol{\hat{x}}_{1:t}^{\mathcal{F}_{\text{SF}}} \
)
\end{equation}$$
$$\boldsymbol{\hat{x}}_t^{\mathcal{F}_{\text{SB}}}=\
\hat{\boldsymbol{T}}^{\text{W}}_{1:t}, \boldsymbol{\hat{M}}$$
$\boldsymbol{z}_t^{\mathcal{F}_{\text{SB}}}=u_{1:t}$, history of odometry and IMU measurements

### Pose estimation with MLE

$$\begin{align}
\hat{\boldsymbol{T}}^{\text{W}}_{1:t}, \boldsymbol{\hat{M}} \ 
&= \operatorname{argmax} \; p (\
\boldsymbol{T}^{\text{W}}_{1:t},
\boldsymbol{M} |\ 
\boldsymbol{\hat{x}}_{1:t}^{\mathcal{F}_{\text{SF}}}, \
\boldsymbol{z}_t^{\mathcal{F}_{\text{SB}}}
)\\

&= \operatorname{argmax} \; p (\
\boldsymbol{\hat{x}}_{1:t}^{\mathcal{F}_{\text{SF}}} | \
\boldsymbol{T}^{\text{W}}_{1:t},
\boldsymbol{M} ) \
p (\hat{T}^{\text{W}}_{1:t} | \
\boldsymbol{z}_t^{\mathcal{F}_{\text{SB}}} \
)
\end{align}$$

### Observation error

$p (\boldsymbol{\hat{x}}_{1:t}^{\mathcal{F}_{\text{SF}}} | \boldsymbol{T}^{\text{W}}_{1:t}, \boldsymbol{M} )$  is the observation likelihood for image feature correspondences given the estimated poses of the camera and the map $\boldsymbol{M}$

The observation error is the reprojection of $p_{k}^{W}$ onto the image $I_{t}$

$$
\delta \boldsymbol{x}_{t,k}^{\mathcal{F}_{\text{SF}}} = \
\boldsymbol{\hat{x}}_{t,k}^{\mathcal{F}_{\text{SF}}} - \
\boldsymbol{x}_{t,k}^{\mathcal{F}_{\text{SF}}}
$$
$$\boldsymbol{x}_{t,k}^{\mathcal{F}_{\mathrm{SF}}}=\boldsymbol{A}\left[\boldsymbol{R}_{W}^{t}|\boldsymbol{t}_{W}^{t}\right]\boldsymbol{p}_{k}^{w}$$
$\boldsymbol{A}$ is the camera matrix, $\boldsymbol{R}_{W}^{t}$ and $\boldsymbol{t}_{W}^{t}$ are rotation and translation parts of $\boldsymbol{T}^t_{W}=(\boldsymbol{T}_t^{W})^{-1}$

In the absence of control commands and IMU/odometry measurements, Eq (Pose estimation with MLE) reduces to the bundle adjustment (BA) problem, which is formulated as a nonlinear optimizaiton.

$${\hat{\boldsymbol{T}}}_{1:t}^{w},{\hat{\boldsymbol{M}}}=\arg\operatorname*{min}_{\boldsymbol{T}_{1:t}^{w},\boldsymbol{M}}\sum_{t,k}{\mathcal{L}}\left(\epsilon_{t,k}^{T}{\scriptstyle\sum_{t,k}^{-1}}\epsilon_{t,k}\right)$$
$\sum_{t,k}$: is the covariance matrix associated with the scale at which a feature has been extracted.
$\epsilon_{t,k}= \delta \boldsymbol{x}_{t,k}^{\mathcal{F}_{\text{SF}}}$
$\mathcal{L}$: is the loss function for $p (\boldsymbol{\hat{x}}_{1:t}^{\mathcal{F}_{\text{SF}}} | \boldsymbol{T}^{\text{W}}_{1:t},\boldsymbol{M} )$

The reprojection error is known to have a non-Gaussian distribution $\phi^{\mathcal{F}_{\text{SF}}}$ in the context of V-SLAM due to the frequent outliers that happen in image correspondences:

$${\hat{\phi}}^{\mathcal{F}_{\mathrm{SF}}}=\mathbb{I}\left({\mathcal{F}_{\mathrm{SF}}}\right)\left[\boldsymbol{z}_{t}^{\mathcal{F}_{\mathrm{SF}}}\right]$$
![[Pasted image 20240604153615.png]]

## Introspection for stereo depth estimation

Introspective perception for GA-Net, a deep neural network for stereo depth estimation, compared to SOTA uncertainty estimation methods.

![[Pasted image 20240606103943.png]]

## Future work

![[Pasted image 20240606104440.png]]

# Conclusions

- Only ${\hat{\phi}}^{\mathcal{F}_{\mathrm{SF}}}$ is calculated but not ${\hat{\phi}}^{\mathcal{F}_{\mathrm{SB}}}$
- According to the equations presented in this paper, is ${\hat{\phi}}^{\mathcal{F}_{\mathrm{SB}}}=\mathbb{I}\left({\mathcal{F}_{\mathrm{SB}}}\right)\left[\boldsymbol{z}_{t}^{\mathcal{F}_{\mathrm{SB}}}, \boldsymbol{\hat{x}}_{t,1:k}^{\mathcal{F}_{\text{SF}}}\right]$?. To do this, we need an equation to minimize like $\epsilon_{t,k}^T{\scriptstyle\sum_{t,k}^{-1}}\epsilon_{t,k}$
- What if I want to use the history of odometry and IMU measurements?
- From what I understand, this paper has described mathematically what any introspection method could do. Their description encompasses other introspection methods, for example Morgan's approach.
- Why SOTA uncertainty estimation (Ensemble, MCDropout) methods were not used for ORB-SLAM? I could try.