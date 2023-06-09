# **Signal for help: real-time detection**

<p align="center">
<img align="right" height=160 src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/95250a662145757e0069db38324ed091de98b063/resources/signal-for-help.png">
  
Artificial Intelligence is an incredibly powerful tool that can be also employed for helping people in case of emergency. Indeed, this project aims to automatically detect the "signal for help" gesture created by the [Canadian Women's Foundation](https://canadianwomen.org/) in 2020. In general, you may use this signal to alert others that you feel threatened and need help, and this is typically convenient in case of domestic violence. 

## Baseline CNN

The signal for help can be imitated by using two signs of the American Sign Language (ASL) one after the other, namely the letters B and E. However, due to the limited amount of good quality data, the letters B and A have been chosen instead. Unlike letter E, in letter A sign the thumb is not hided under the other fingers; however, the baseline model reached an acceptable accuracy in recognizing the help gesture.

A CNN has been designed as baseline model to discriminate beetween the two ASL gestures and has been trained on a modified version of the [Hand Reader Dataset](https://github.com/tofighi/Hand-Reader-Dataset). You can find the modified dataset in the `baseline/hand-reader-dataset` folder of this repository. The dataset consists of a subset of the original images, corresponding to the classes "A" and "B" only (see the first row of images below). Moreover, the images have been cropped to a square format and the background has been lightened (see the second row of images below). In this way, the model can recognize more easily the gestures appearing in front of a light background, which is indeed to the most frequent setting for a webcam video frame.

<p align="center">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/2168b670cd07b73dcebc6113963bffb265aeda95/resources/dataset.png" width="80%">
</p>

The CNN discriminator takes in input a patch that is automatically detected by the [Mediapipe hand-landmarks-detector](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) within an image frame, in two different possible settings:
  1. The image frame is a single photograph generated with the `take_photo()` code snippet available in Google Colab. In this way you can detect the ASL signs "A" and "B" as individual gestures.
<p align="center">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/e10b00620755c55e27b18877b70b8ffdde907de8/resources/sampleA.png" width="40%">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/e10b00620755c55e27b18877b70b8ffdde907de8/resources/sampleB.png" width="40%">
</p>

  2. The image frame is continuously updated according to your real-time webcam video stream (generated via the `video_stream()` code available [here](https://github.com/theAIGuysCode/colab-webcam)). In this way the signal for help is detected whenever you show on camera the ASL letters "B" and "A" in sequence.

Please note that in order to run the experiments contained in the `baseline-help-sign-detection.ipynb` notebook, you have to meet the following requirements: choose a light background for your video and record the video with a good light condition.

## YOLO (v4) transfer learning on custom dataset

<a target="_blank" href="https://colab.research.google.com/github/silviapoletti/Help-sign-real-time-detection/blob/cd2fe9fe9d6e542b8c09c2dbfd0b23b0ced4beb8/yolov4_help_sign_detector.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

A more sophisticated approach is to finetune the YOLO (v4) state-of-the-art real-time object detector (Darknet repository [here](https://github.com/AlexeyAB/darknet)) on a custom dataset containing samples of the two signs appearing in the signal for help gesture. Then, the model has been tested in the same two settings described in the previous section.

The custom dataset has been generated and labeled with the use of the [LabelImg](https://github.com/heartexlabs/labelImg#labelimg) tool.

For a complete a detailed description of the steps needed to perform transfer learning, please refer to this [guide](https://medium.com/p/61a659d4868#f7ec).
You can find the required additional files that are not present in the Darknet repository in the `resources` folder of this repository.

The following record shows the performance of the finetuned YOLO model during a real-time webcam video stream with a mediocre light condition and a cluttered background.

https://user-images.githubusercontent.com/65509198/232893783-1adc45b4-74a4-4c2d-9902-b985ed689982.mp4
