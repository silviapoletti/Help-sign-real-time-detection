# Signal for help: real-time detection

Artificial Intelligence is an incredibly powerful tool that can be also employed for helping people in case of emergency. Indeed, this project aims to automatically detect the "signal for help" gesture created by the [Canadian Women's Foundation](https://canadianwomen.org/) in 2020. In general, you may use this signal to alert others that you feel threatened and need help, and this is typically convenient in case of domestic violence. 

The signal for help (see the image below on the left) can be imitated by using two signs of the American Sign Language (ASL), namely the letters A and B (see the images below on the right) one after the other.

<p align="center">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/95250a662145757e0069db38324ed091de98b063/resources/signal-for-help.png" height=300>
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/e6957ba06275f95b0b7c04dacbcba32c95cee645/resources/ASL.jpg" height=300 style="padding-left:50px">
</p>

Therefore, a CNN has been designed to discriminate beetween the two ASL gestures and has been trained on a modified version of the [Hand Reader Dataset](https://github.com/tofighi/Hand-Reader-Dataset) (see the first row of images below). You can find the modified dataset in the `hand-reader-dataset` folder of this repository. The dataset consists of a subset of the original images, corresponding to the classes "A" and "B" only. Moreover, the images have been cropped to a square format and the background has been lightened (see the second row of images below). In this way, the model can recognize more easily the gestures appearing in front of a light background, which is indeed to the most frequent setting for a webcam video frame.

<p align="center">
  <img src="https://github.com/tofighi/Hand-Reader-Dataset/blob/aad4a81ade6cfe5c8b963ac3837b769a5bb623b0/hand-reader-dataset/A/00000.jpg" width="20%">
  <img src="https://github.com/tofighi/Hand-Reader-Dataset/blob/aad4a81ade6cfe5c8b963ac3837b769a5bb623b0/hand-reader-dataset/A/00001.jpg" width="20%">
  <img src="https://github.com/tofighi/Hand-Reader-Dataset/blob/aad4a81ade6cfe5c8b963ac3837b769a5bb623b0/hand-reader-dataset/B/01000.jpg" width="20%">
  <img src="https://github.com/tofighi/Hand-Reader-Dataset/blob/aad4a81ade6cfe5c8b963ac3837b769a5bb623b0/hand-reader-dataset/B/01001.jpg" width="20%">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/ae8d17e5d83b78bfa9c3b4bb50907d97fea7e7b8/hand-reader-dataset/A/00000.png" width="20%">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/ae8d17e5d83b78bfa9c3b4bb50907d97fea7e7b8/hand-reader-dataset/A/00001.png" width="20%">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/ae8d17e5d83b78bfa9c3b4bb50907d97fea7e7b8/hand-reader-dataset/B/01000.png" width="20%">
  <img src="https://github.com/silviapoletti/Help-sign-real-time-detection/blob/ae8d17e5d83b78bfa9c3b4bb50907d97fea7e7b8/hand-reader-dataset/B/01001.png" width="20%">
</p>


<br/>
