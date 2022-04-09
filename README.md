# heart_rate_ppg_camera
Heart rate estimation using PPG data from Mobile Camera
AIM:
To Record a 15 second long video by keeping finger over the camera with flash on. To use the video recordings to perform PPG and estimate heart rate.


Link to video demonstration: 

Approach:

1. Finger was put on camera and a 15 second video was recorded with flash on in each case.
2. The video was imported to python using open CV2 and a video data object was created. FPS, frame count were determined.
3. The first few frames and last few frames were dropped as a data pre processign measure as they contain most of the error. e.g - putting finger and removing finger, stabilizing time etc
4. For each image of the video, pixels in thge middle were selected, and average was calculated for Red, Green and Blue colors
5. An array for each color was maintained to store average value. The number of items in the array were equal to the number of images.
6. The array data was plotted seperately for reference.
7. The red array was selected for further processing and determination of results as Red gave best results graphically [ASSUMPTION 1].
8. The array is now treated as a signal.
9. The signal is passed through a Lowpass filter, followed by a high pass filter to remove unwanted frequencies. The constants were roughly determined.
10. Then, the signal was squared to elongate it, so that it is easy to determine peaks [ASSUMPTION 2]
11. A moving average filter was applied to remove any unwanted spikes. The window size was roughly estimated.
12. The signal was printed for reference.
13. Peaks were detected and average time between peaks were calculated.
14. Heart rate was calculated and compared with real data to calculate error.
15. The process was repeated for 4 more different person.


OBSERVATION:

SERIAL NO.  NAME       AGE    GENDER    CALCULATED HR IN BPM   REAL HR IN BPM    %ERROR mean absolute
1          divyanshu    22      M		      86		                	84		                2.79
2	         ratul	      22	    M		      88			                79		                11.39
3          pranjal      22 	    F		      65			                72		                9.72
4	         mukib	      23      M         77    			            69		                 11.59
5          ambarish     22      M         73			                75		                 2.67


Mean of all errors: 7.63%

CONCLUSION:
Position of finger plays important role in data quality, placing finger on camera only gave better results than placing finger on both
camera and flash. The pressure applied by finger should be gentle. Flash should be ON otherwise error is more than 25%. 
Light skin color are better as they let in and out more light. 
