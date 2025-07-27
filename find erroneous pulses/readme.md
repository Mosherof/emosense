# Find Erroneous Pulses

This pipeline is used to compare the information recorded during the trial to our expected results. It is a more robust test than the previous method which relied solely on counters.

I previously used code in MATLAB to align the expected number of video clips to the actual recorded values. The expected values could be obtained through a csv file in the following form:
<pre>
| trial |             clips                |
|   1   | [xxx.mp4, xyx.mp4, ..., yxy.mp4] |
|   .   |                .                 |
|   .   |                .                 |
|   .   |                .                 |
|   7   | [yyx.mp4, yxx.mp4, ..., xxy.mp4] | 
 </pre>, where there was a unique set of videos in each of the 'clips' row. 
The recorded values were of the following form:
<pre>
| event_coded | latencies |
|     3       |  3424     |
|     1       |  5345     |
|     4       |  6345     |
|     4       |  8538     |
|     2       |  9998     |
|     3       |  10166    |
|     1       |  12389    |
|     .       |           |
|     .       |           |
|     .       |           |
|     2       |  54567    |
|     3       |  61557    |
</pre>, where 2's and 3's represented events inbetween video stimulus (trials). 1's represented the first video of a trial and 4's represented the following videos within the trial.

Thus, I could parse information from the expected to determine if there were any differences. 

However, when the expected number of pulses differed from the recorded, there was no way to  verify the "true" markers. This code takes into account the length (in seconds) of each clip. Latencies refers to the number of measurements taken per second, and therefore, comparable as each clip's duration was given in a table of the following form:
 <pre>
|clip name| duration |
| xyz.mp4 |   3.45s  |
|   .     |   .      |
|   .     |   .      |
|   .     |   .      |
| zzz.mp4 |   3.2 s  |
</pre>

The algorithm outputs a dataframe which isolates the seconds inbetween pulses for each trial and seconds of each video. Therefore, a relationship can be determined as to which pulses represents which video.
