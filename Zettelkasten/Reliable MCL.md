202404231515

Status: #idea

Tags: [[localization]] [[nonintegritynorintrospection]] [[fault detection]] [[reliability]]

# Original Text

# In my own words

This paper presents robust localization (dynamic environments), reliability estimation, and quick re-localizacion, simultaneously.

This paper is based on MCL localization

This paper states that improving the measurement model is effective to improve localization robusness. However, their approach extneds the graphical model.

They mention that confidence and reliability are different terms. Confidence refers to uncertainty and it can be calculated from the pose estimation uncertainty. They states that reliability cannot be calculated. Their approach employees a localization classifier and estimates reliability using the classifier.

**More features about the paper**

- It is focused only on AMCL localization.
- It does not use multi-sensor data for estimating reliability.
- It is based on Bayesian filtering. That is why they can compute the uncertainty of the classifier.
- It uses an inertial navigation system (INS) and LiDAR. INS measurements are included as u and LiDAR measurements as z.
- Do they still train the network in simulated indoor environment?

**My Questions**

Q1: How come reliability cannot be calculated? Classifiers perform calculations, or not?
# References