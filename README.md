# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

  ## PROGRAM:
Developed by: DANICA CHRISTA
Register Number: 212223240022

```
# Import libraries and Load the Face Image
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('643.JPG')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
```

![Screenshot 2025-04-15 092701](https://github.com/user-attachments/assets/1bf61351-485d-419e-843a-4d84840fbb3f)



```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))
```

![Screenshot 2025-04-21 175104](https://github.com/user-attachments/assets/4052c26e-7b08-4bb4-b6c1-293d351776ca)



```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))

# Separate the Color and alpha channels
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

# Display the images for clarity
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
```

![Screenshot 2025-04-21 175114](https://github.com/user-attachments/assets/8d0cdfff-c1d8-491c-a10e-ed8fd3d6c69a)



```
faceWithGlassesNaive = faceImage.copy()
# Replace the eye region with the sunglass image
faceWithGlassesNaive[150:220, 120:310]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
```

![Screenshot 2025-04-21 175129](https://github.com/user-attachments/assets/3a9ec137-a378-4d7d-a166-c77c8c8109c0)



```
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[150:220, 120:310]
maskedEye = cv2.multiply(eyeROI,(1-glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```

![Screenshot 2025-04-21 175137](https://github.com/user-attachments/assets/d0f8fc9d-ecd7-4a94-bb4d-fad8ffed9726)



```
faceWithGlassesArithmetic[150:220, 120:310]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```

![Screenshot 2025-04-21 175156](https://github.com/user-attachments/assets/9d0f6d41-7351-4619-82ed-cf7ff97c80c4)


 


