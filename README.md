<h1>
The Inertial Sensor Signals Processing
<img src="https://media.giphy.com/media/ClI4dtCC0E9AZsAVss/giphy.gif" width="40px">
</h1>

- this project is based on [*Smartphone-Based Recognition of Human Activities and Postural Transitions Data Set*](http://archive.ics.uci.edu/ml/datasets/smartphone-based+recognition+of+human+activities+and+postural+transitions) :point_left: all descriptions are here
- includes the use of csv files, data processing algorithms, windowing, time and frequency signals, data visualisation
- final data is ready to use in *Neural Network Models*
- the project is focused on the classification of 6 activities: 3 dynamic like walking, walking upstairs, walking downstairs, and 3 static like standing, sitting, laying
- data was registered by sensors from smartphone

<h2>
Technologies
<img src="https://media.giphy.com/media/Vf3ZKdillTMOOaOho0/giphy.gif" width="45px">
</h2>

- language: Python 3.10.1
- main libraries: TensorFlow, Keras, Matplotlib, Seaborn, Pandas, Numpy
- computing platform: Jupyter Notebook

<h2>
More about the project
<img src="https://media.giphy.com/media/9JZ2yaCjnoCpSQ4tWv/giphy.gif" width="45px">
</h2>

Stages of this data processing project:

**1. Opening .csv files and putting all signal samples and labels into DataFrames**

:small_orange_diamond: DataFrame with raw signals

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/signal_df.png" width="350px">

:small_orange_diamond: DataFrame with labels

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/labels_df.png" width="350px">

**2. Raw signals visualisation**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/acc_signal.png" width="600px">
<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/gyr_signal.png" width="600px">

**3. Noise reduction and extraction of time signals components:**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/raw.png" width="550px">

- *median_filter()* - median filter

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/median.png" width="550px">

- *butterworth3rd()* - low-pass 3rd order Butterowrth filter to reduce noises above 20 Hz

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/butter.png" width="550px">

- *butterworth()* - high-pass filter to separate body and gravity components from the total acc. signals (cutoff - 0.3 Hz)

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/total.png" width="550px">
<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/body.png" width="550px">
<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/gravity.png" width="550px">

- *jerk_signal()* - the jerk signal (da/dt) where: da = d(signal) and dt=1/fs
- *magnitude()* - the euclidean magnitude for 3 axes signals

**Finally, the result for time signals:**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/t_signal.png" height="300px">

**4. Windowing (fixed-width sliding windows)**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/windowing.png" height="250px">

- Windowing the signal with a span of 2.56 sec (2.56sec × 50Hz = 128 cycles) and an overlap of 50%
- **Each window has 128 elements**
- As a result, 10399 samples were obtained

**5. Converting the time signals to frequency singals**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/f_signal.png" height="250px">

**6. Measures for computing feature vectors**

Feature extraction from signals to prepare the data for the Neural Network - **summary 481 signals features**.

- *mean_f()* - arithmetic mean
- *std_f()* - standard deviation
- *mad_f()* - median absolute deviation
- *min_f()* - lowest value 
- *max_f()* - largest value
- *energy_f()* - average sum of the squares
- *iqr_f()* - interquartile range
- *ropy_f()* - signal entropy
- *sma_f()* - signal magnitude area
- *corr_axis()* - Pearson correlation coefficient (just 3 axes time signals)
- *maxFreqInd()* - largest frequency component (just freq. signals)
- *meanFreq()* - frequency signal weighted average (just freq. signals)
- *skewness()* - frequency signal Skewness (just freq. signals)
- *kurtosiss()* - frequency signal Kurtosis (just freq. signals)
- *energyBands()* - spectral energy of a frequency band (just 3 axes freq. signals)
- *angle_features()* - angle between to vectors 

**7. Results**

:small_orange_diamond: **General Data**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/g_data.png" width="400px">

- :white_check_mark: after signal processing it's 481 features for each window
- :white_check_mark: it's 10399 samples which are useful to train and test cnn 
- :white_check_mark: features are saved in the file: 'global_data.csv'
- :white_check_mark: labels for each window are saved the file: 'global_labels.csv'
- :white_check_mark: this database is ready to use in *Neural Networks Models*

<h2>
  License
</h2>

[MIT License](https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/LICENSE.txt)

<div align="center">
  <img src="https://media.giphy.com/media/U4PYZB2K3qY8aSPTYF/giphy.gif" width="200px">
</div>






