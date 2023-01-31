[Design of Magnetic Levitation Controllers UsingJacobi Linearization, Feedback Linearization and Sliding Mode Control](http://educypedia.karadimov.info/library/DesignOfMagneticLevitationControllersUsingJacobiLinearizationFeedbackLinearizationAndSlidingMode.pdf)

[How SpaceX lands Starship -  optimization](https://thomas-godden.medium.com/how-spacex-lands-starship-sort-of-ee96cdde650b)
	-	 [HN DIscussion](https://news.ycombinator.com/item?id=27148296)

[Intro to Trajectory Optimization in an hour ](https://www.youtube.com/watch?v=wlkRYMVUZTs)

[Scaling PID Tuning Parameters for Different Controller Sample Rates](http://support.motioneng.com/downloads-notes/tuning/scaling_pid_param.htm)

[PIDTuner](https://pidtuner.com/#/) - A web app to automatically find the optimum P, I, D values. Some [videos are available](https://www.youtube.com/channel/UCkRD7FztiFOdX50BUsOkcSQ). [HN Discussion](https://news.ycombinator.com/item?id=27273399) about PIDTuner

Improving PID loop implementation - notes by Arduino PID library author - http://brettbeauregard.com/blog/2011/04/improving-the-beginners-pid-introduction/

[Probably the best Simple PID tuning rules in the world](https://folk.ntnu.no/skoge/publications/2001/tuningpaper_reno/tuningpaper_06nov01.pdf)

[PID Control loop mechanism](https://vaclavkosar.com/ml/PID-controller-control-loop-mechanism) - [HN Discusion](https://news.ycombinator.com/item?id=27318942)

[Servo Basics for the Layman](https://support.controltechnologycorp.com/customer/elearning/registered/servoBasicsForTheLayman.pdf)  - explains PID - motion control-synchronisation etc 

[Everything you need to know about control theory](https://youtu.be/lBC1nEq0_nk) -  Excellent video giving a Layman's overview of all control techniques

Model Predictive Path Integral control  - https://bostoncleek.github.io/project/mppi
https://github.com/bostoncleek/ROS-Turtlebot-Navigation/tree/master/controller

[Simple PID library in python](https://github.com/m-lundberg/simple-pid)
- Make sure to use disable/enable `auto_mode` , if you are not running it continuously. Else the (integral?) errors adds up and causes a jump on next step.
