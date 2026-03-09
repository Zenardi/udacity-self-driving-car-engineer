# Parameter Optimization

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=A2b3F5Ae53Y)

## Summary

**Summary of RAN Procedure Modification and Twiddle Algorithm**

This project involves modifying the RAN procedure to input a parameter vector of three parameters. The goal is to implement the twiddle algorithm with a tolerance and threshold of 0.001, which finds the optimal parameters for the controller.

### Key Concepts

* **RAN Procedure**: A modified version of the RAN procedure that inputs a parameter vector of three parameters.
* **Print Flag**: A flag set to false by default, used to control the output format (degrees or variance).
* **Twiddle Algorithm**: An algorithm that finds the optimal parameters for the controller with a tolerance and threshold of 0.001.
* **Parameter Selection**: The process of selecting the best parameter values for the controller.
* **Cross Stick Arrow**: A measure used to evaluate the performance of the controller, which quickly goes to zero after a few iterations.

### Practical Notes

To implement the twiddle algorithm, you will need to:

* Modify the RAN procedure to input a parameter vector of three parameters
* Implement the twiddle algorithm with a tolerance and threshold of 0.001
* Use a print flag to control the output format (degrees or variance)
* Evaluate the performance of the controller using the cross stick arrow measure

Note: The final control error between time step 100 and 200 should be really small, indicating that the controller is effective in tracking the desired location.

## Transcript

<v English>So to implement this I’ve modified the RAN</v> <v English>procedure to input a parameter vector of three</v> <v English>parameters. And for reasons that will be obvious</v> <v English>later, I have a print flag that I default to false.</v> <v English>I have the same initial parameters as before,</v> <v English>speed and arrow cross stick arrow – into the</v> <v English>cross stick arrow, I set my fifth parameter</v> <v English>and to make it a little bit more obvious how</v> <v English>what the effect of parameter selection has on</v> <v English>my arrow. I also set the total number equations</v> <v English>to N times 2 and when I count the total cross</v> <v English>stick arrow, I only counted from step N 1,</v> <v English>so I give the algorithm a chance to convert to</v> <v English>zero for N steps, they don’t count the cross</v> <v English>stick arrow, but like to know how the cross</v> <v English>stick arrow evolves quite dramatically from</v> <v English>step 101 on to 200. If the print flag is set, I</v> <v English>set the output here in degrees and not in variance</v> <v English>and I return my average arrow before value.</v> <v English>So I wanted to write the routine twiddle and</v> <v English>the routine should find the optimal parameters</v> <v English>and return them to me. So I want you to</v> <v English>implement the twiddle with a tolerance and</v> <v English>threshold of 0.001.

In one twiddle, it shows</v> <v English>the parameters over time and the cross</v> <v English>stick arrow. And this cross stick arrow</v> <v English>very quickly goes to zero. In fact after a</v> <v English>few iterations, 107 in my implementation</v> <v English>we get a cross stick arrow of 3.611 to the</v> <v English>minus 17th. And here is the typical control</v> <v English>one, you see my X, my Y, my orientation,</v> <v English>my drift is constant, that’s my constant</v> <v English>drift parameters and the beginning of the</v> <v English>arrows are 195 on average. But after a short</v> <v English>amount of time, you find that my Y arrow</v> <v English>goes down to 10 to the minus 6 and stays</v> <v English>there, which means our controller is really,</v> <v English>really good in tracking our desired location.</v> <v English>In our final control error between time step</v> <v English>100 and 200 is 3.611.

So I wanted to</v> <v English>implement twiddle, we might change something</v> <v English>on the vowel set up, but when you run it,</v> <v English>it will be such that if you want a full PED</v> <v English>controller and find the optimal parameters</v> <v English>that the final control error, will be really, really</v> <v English>small and that’s how we’ll checking.</v>

## Additional Content

In the following quiz you'll implement the twiddle algorithm for a PID controller. Additionally, the robot has a steering drift!
