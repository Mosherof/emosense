# Find Erroneous Pulses

This pipeline is used to compare the information recorded during the trial to our expected results. It is a more robust test than the previous method which relied solely on counters.

I previously used code in MATLAB to align the expected number of video clips to the actual recorded values. The expected values could be obtained through a csv file in the following form:
| trial |             clips                |
|   1   | [xxx.mp4, xyx.mp4, ..., yxy.mp4] |
|   .   |                .                 |
|   .   |                .                 |
|   .   |                .                 |
|   7   | [yyx.mp4, yxx.mp4, ..., xxy.mp4] |, where there was a unique set of videos in each of the 'clips' row. 
The recorded values were of the following form:
| event_coded | latencies |
|     3       |  3424     |
|     1       |  2345     |
|     4       |  3345     |
|     4       |  2538     |
|     2       |  1998     |
|     3       |  1466     |
|     1       |  2389     |
|     .       |           |
|     .       |           |
|     .       |           |
|     2       |  4567     |
|     3       |  1557     |
 

However, when the actual was less than the expected, there was no way to 
verify the "true" markers. This code takes into account the length (in seconds) of each clip and compares it to 
 True values were recorded in a relational table of the form:
|clip name| duration |
| xyz.mp4 |   3.45s  |
|   .     |   .      |
|   .     |   .      |
|   .     |   .      |
| zzz.mp4 |   3.2 s  |
