202404121635

Status: #idea

Tags:

# Original Text

# In my own words

This paper proposes to add, to ORB-SLAM, the capability of knowing when a next step is dangerous for the localization task. It also gives ORB-SLAM the ability of avoiding trajectories that could put in danger the localization task. To do this, authors used a Deep Q-learning Neural Network (DQN) to score the safety of the a set of discrete movements (actions) of the robot (forward, backward, left, right, ...). The output of DQN is quality value (Q) for each of the discrete movements. 

The "health" of the visual tracker is quantified by the number of overlaping amount of keypoints between two consecutive images ($N_{ov}$) and the SLAM status indicator ( $\psi$). With these two variables, a reward function, r, is proposed.

$$r (s, a) = η_1 N_{ov} + η_2ψ + η_3$$
To train the DQN you have to keep moving the robot to assure t two variables keep high. You have to keep moving the robot for some hours.

## Possible weaknesses of this paper

You have to keep driving the robot for several amount of hours to train the network.

The values  $η_1$, $η_2$ and $η_3$ are only presented.Authors do not mention how to calculate them.

When $N_{ov}$ and $ψ$ are good enough? Their description is cryptic.

Training is carried out with only a simulator

Experiments are carried out only in indoor environments, no challenging environments.

How to know if previous thresholds will work in other environments?
# References

[[@naveedDeepIntrospectiveSLAM2022]]