202402231610

Status: #idea

Tags: [[localization]]

# Original Text
Here the initial pose of the robot is unknown. The robot is
initially placed somewhere in its environment, but it lacks knowledge of where
it is. Approaches to global localization cannot assume boundedness of the pose
error. As we shall see later in this chapter, unimodal probability distributions are
usually inappropriate. Global localization is more difficult than position tracking;
in fact, it subsumes the position tracking problem.

# In my own words
The robot is located somewhere in an environment. There is a map reference frame which is the (0,0,0) but since you don't know the robot's position, you either know where the map reference frame is. The robot goes estimating better its position while it senses the environment.
# References
https://www.youtube.com/watch?v=8VJ-A9OlhAE&t=71s
[[@thrunProbabilisticRobotics2006]]
