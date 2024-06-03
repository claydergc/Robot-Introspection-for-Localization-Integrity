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
$\hat{\phi}^{\mathcal{F}}=\mathbb{I}(\mathcal{F}[\boldsymbol{z}_t^{\mathcal{F}},\boldsymbol{\hat{y}}_t^{\mathcal{F}}])$

## Example

$\mathcal{F}(\cdot)$: It can be a human tracking algorithm
$\boldsymbol{\hat{x}}_t^{\mathcal{F}}$: 3D pose of pedestrians
$\boldsymbol{\hat{y}}_t^{\mathcal{F}}$: Bounding boxes of pedestrians
$\boldsymbol{z}_t^{\mathcal{F}}$: Image

# In my own words

# References