202403151632

Status: #idea

Tags: [[Integrity]] [[Integrity Risk (IR)]]

# Original Text

# In my own words

This paper focuses on the calculation of the Integrity Risk (IR)

$$
\begin{equation}
\textrm{IR}=Pr(\textrm{PE}>\textrm{PL}) \tag{1}
\end{equation}
$$

which is the probability (Pr) that the position error (PE) is greater than the protection level (PL). This IR must be less or equal to the target integrity risk (TIR or IR_max).

## 1st contribution: Fault Detection and Exclusion (FDE)

The first contribution of this paper is the use of a fault detection and elimination technique which is based on the Mahalanobbis distance to discard some measurements from the extended information filter (improved kalman filter). With this method faulty measured are excluded from in the state space using a residuals threshold. This threshold is found using a chi-square distribution.

## 2nd contribution: Calculation of PL

The protection level (PL) of an estimated position is calculated with that position's uncertainty distribution (usually a Gaussian). We need the TIR or IR_max to compute the probability bounded by the TIR.

What this paper proposes is to use a student's t-distribution instead of a Gaussian distribution to model the poses errors. The use of the student's t-distribution changes the values computed for Eq. $\eqref{ir1}$ because this distribution has heavier tails. So, some errors could not be lower-bounded.

# References

[[@alhageLocalizationIntegrityIntelligent2022]]