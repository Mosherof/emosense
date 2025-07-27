# Emosense
Pipelines and code that streamlined the preprocessing of emosense.

# Objective of Emosense
Emosense is a research project I am helping with as a volunteer at the University of California, San Francisco; More specifically, [Neuroscape](https://neuroscape.ucsf.edu/about/). 
The goal of the project is to connect brain signals picked up by EEG to positive human emotions. Various video clips are shown to individuals while wearing EEGs. The clips are intented to evoke specific categorical emotions. 

# Preprocessing
The study was comprised of 5 different participants, each having 4 sessions of responses to emotion-inducing videos. These 4 sessions each have 7 smaller blocks each containing 6 trials. Within each trial, various video clips were spliced together to create continuous brain signals for 30-60 seconds at a time. Inbetween each trial, there was a period of time to rest. The study recorded the change between videos and trials using "pulses" with the following format:
1. 1 pulse: the beginning of a video.
2. 2 pulses: the beginning of the rest period.
3. 3 pulses: the begginning of the crosshair.
Pulses were automatically recorded when the video screen went dark, and therefore, prone to errors. This is problematic and directly causes unclean data. When I joined the team, my original task was to manually compare the number of pulses to the known amount of clips for the trial. If they did not match, the block excluded from further analysis.

Counting and comparing thousands of values by hand appeared to be a tedious and unverifiable process; therefore I took the initiave to streamline the process in a series of smaller steps. Additionally, I developed a method to fix datasets where extra pulses were added by the machine. This resulted in an increase of usable data by 50%.
