202404231028

Status: #idea

Tags: [[localization]] [[nonintegritynorintrospection]] [[fault detection]] [[reliability]]


# Original Text

# In my own words

In this approach, a convolutional neural network (CNN) is used to make decision whether the localization process has failed or not. We train the CNN using a dataset that includes successful localization results and faults.

Since the decision made by the CNN may contain some noise, the robot's pose and reliability estimate are based on the decision using a new graphical model based on the Rao-Blackwellized particle filter.

This new model is testes in simulations and actual environments. This method show that it can be used as an exact criterion for detecting localization faults.

The proposed approach is trained in simulated environments, but tests are made on actual environments.

**More features about the paper**

- It is focused only on laser scans matching approach.
- It finds mismatches using a CNN. So it needs the map a priori.
- The CNN can distinguish whether the localization has failed or not. But this output contains nosie.
- The reliability of the CNN is used as a probabilistic variable (random variable). Not used directly from the output
- This probabilistic variable is an input for the graphical model based on the RBPF.
- This method is a fault detection method.
- Reliability, r, ranges from 0 to 1. Then they estimate the probability distribution for r at the current time t.
- The training dataset was created using a simulation. First the OGM was created with GMapping

Keywords: fault detection, reliability

**My Questions**

Q1: Do they use sensor fusion? No, only lidar. Besides it is only based on scan matching algorithms.
Q2: Is it enough to train the model in simulated environments? Apparently, yes. But further evaluation is needed.
Q5: Was this method only tested at indoor environments? Yes.
Q4: Does this method only work for the RBPF? Yes.
Q5: Why don't they use the error distribution from the particle filter? I dont know
Q6: Does this method use reliability as several dimensions? No, reliability only ranges from 0 to 1. It does not detect the type of fault.
# References

[[@akaiSimultaneousPoseReliability2018]]