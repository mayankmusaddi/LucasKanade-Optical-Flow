# LucasKanade-Optical-Flow

This is an implementation of the Optical Flow Algorithm by Lucas Kanade which has been used to do the following -
 - Detection and segmentation of moving objects in a video
 - Tracking of objects in a video sequence

## Optical Flow Function

http://www.inf.fu-berlin.de/inst/ag-ki/rojas_home/documents/tutorials/Lucas-Kanade2.pdf

Implemented according to the above link, the optical flow function takes in 2 images and returns the velocity vectors corresponding to the Lucas Kanade Optical Flow Algorithm.

The function is constructed in 2 parts:

For faster computation we could use cv2's goodFeaturestoTrack function and implement our logic only on those points.

However we could also iterate over every pixel of the image and implement the logic to find the velocity vectors for that point. These vectors are only taken for those points which pass a certain threshold

## Object Tracking

We use the above optical flow algorithm implemented for two consecutive image over a video for tracking the movement of objects.

For doing so we have first converted the input video into frame wise images. For every consecutive frames we evaluate the optical flow. Using the velocity vectors obtained from the optical flow results, we construct a segmented images by thresholding the magnitude of the vectors. We find the connected compoenents from the thresholded image and put a bounding box for every big enough sized component. This bounding box images are assembled in the `output` folder from which the video is reconstructed using imageToVideo function