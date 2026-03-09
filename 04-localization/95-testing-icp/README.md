# Testing ICP

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=FgVEuChHcEc)

## Additional Content

## Testing ICP

Once you have completed the filter for the input scan and ICP function, the algorithm can be tested by compiling and running and then pressing "i" on the keyboard. When you are able to successfully align the input scan with the map and overlap the green and red boxes there are other controls for adjusting and doing further testing. 

## Testing Different Initial Offsets

The input scan can be manually translated and rotated to test the limit of how well ICP can converge depending on the starting offset. To move the input scan the following keyboard keys can be used.

### Translate (UP/DOWN LEFT/RIGHT Arrow Keys)

### Rotate ( K/L)
## Saving and Resetting Initial Pose

To reset the initial pose back its last saved value or to save a new initial pose the following keys can be used.

### Reset Pose ( Space )

### Save Pose ( X )

## Running Tests

Each time "i" is pressed the ICP algorithm is set to run until the delta position becomes small enough, meaning ICP has converged to some position. The ouput from the run is the time it takes and number of cycles until convergence as well as the final pose error. You can use these metrics to optimize the scan matching process. Since you will be using scan matching in real time for the final project in this course the total time is an important consideration. Below is a video of what it looks like using ICP to align the input scan at various starting pose offsets to the map, along with the metrics each test generates.
