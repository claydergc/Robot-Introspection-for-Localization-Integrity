202402221736

Status: #idea

Tags: [[slam]] [[localization]]

# Original Text
The keyword here is “loop closure”: if we sacrifice loop closures, SLAM reduces to odometry. In early applications, odometry was obtained by integrating wheel encoders. The pose estimate obtained from wheel odometry quickly drifts, making the estimate unusable after few meters [128, Ch. 6]; this was one of the main thrusts behind the development of SLAM: the observation of external landmarks is useful to reduce the trajectory drift and possibly correct it [185].

Recent odometry algorithms are based on visual and inertial information, and have very small drift (< 0.5% of the trajectory length [83]). Hence the question becomes legitimate: do we really need SLAM?

Visual-inertial navigation (VIN) is SLAM: VIN can be considered a reduced SLAM system, in which the loop closure (or place recognition) module is disabled

# In my own words
Odometry-based localization is SLAM but without loop closure.

# References
[[@cadenaPresentFutureSimultaneous2016]]