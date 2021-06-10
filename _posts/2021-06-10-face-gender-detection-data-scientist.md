---
title: "Face Gender Detection With cvlib"
excerpt: "Are there more male faces of data scientists on google search"
last_modified_at: 2021-06-09 18:18:28
excerpt_separator: "<!--more-->"
categories:
  - Tips
tags:
  - Computer Vision
  - Image Data
  - Face Detection
  - Gender Detection
toc: true
header:
  teaser: /assets/images/mm-free-feature.jpg
---

## What this does
Given an image, perform Face detection and gender detection with pretrained computer vision models


## The use case
To make it more fun, I will apply these techniques to find out if there are more male or female faces of data scientists on search engine.

## How to do this
#### Step 1: Get some images of data scientists
![Google Image Search](/assets/images/google-image-search-data-scientist.png)

This is the image search result of keyword 'Data Scientist'. We want to download a lot of these images without having to manually right-click and download. To do this you can use one of the following solutions. 
* Paid solutions, some could be free of charge depends on your subscription
    * [Bing Image Search API by Azure](https://www.microsoft.com/en-us/bing/apis/bing-image-search-api)
    * [Custom Search JSON](https://developers.google.com/custom-search/v1/overview)
* Python packages that's web crawler under the hood
    * [google_images_download](https://pypi.org/project/google_images_download/)
    * [simple-image-download](https://pypi.org/project/simple-image-download/) I'm using this
* Write your own web crawler
    * Use [requests](https://docs.python-requests.org/en/master/) and [Beautiful Soup](https://pypi.org/project/beautifulsoup4/)
    * Use [Selenium WebDriver](https://www.selenium.dev/documentation/en/webdriver/)

Here is sample code to download images using simple-image-download package

```python
from simple_image_download import simple_image_download as simp
response = simp.simple_image_download
response().download(keywords='Data Scientist', limit=500, extensions={'.jpg', '.png', '.ico', '.gif', '.jpeg'})
```
Wait for the progress bar to reach 100%, and voila! you've got enough image data to proceed.

#### Step 2: Find faces in image
Now let's crop the human faces in these images. To do this we will use the [cvlib](https://pypi.org/project/cvlib/) in python

```bash
pip install opencv-python tensorflow
pip install cvlib
```
First to find all the human faces in an image, if there is any.
```python
import cvlib as cv
import cv2

#filepath is path to one image, in this example, filepath is 'simple_images/Data_Scientist/Data Scientist_501.png'
img=cv2.imread(filepath)
faces, confidences = cv.detect_face(img)
```

faces is a list of tuples that contains the 4 vertices of a rectangle around human face. Use the code below to draw a rectangle around face detected. This is optional.

```python
import matplotlib.pyplot as plt

f=faces[0]
padding = 20
(startX,startY) = max(0, f[0]-padding), max(0, f[1]-padding)
(endX,endY) = min(img.shape[1]-1, f[2]+padding), min(img.shape[0]-1, f[3]+padding)

# Rectangle cropping over face
cv2.rectangle(img, (startX,startY), (endX,endY), (0,255,0), 2)

# OpenCV reads and displays an image as BGR format. Converting to RGB to plot with matplotlib
img=cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
face_crop = np.copy(img[startY:endY, startX:endX])
plt.imshow(img)
plt.show()
```
{% capture fig_img %}
![Rectangle Over Face]({{/assets/images/rectangle-over-face.png | relative_url }})
{% endcapture %}

Image by <a href="https://pixabay.com/users/alyibel-3625842/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2326419">Alyibel Colmenares</a> from <a href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2326419">Pixabay</a>


#### Step 3: Face gender classification
Now we pass the cropped face images to a gender classifier.

```python
# Apply gender detection
label, confidence=cv.detect_gender(face_crop)
plt.imshow(face_crop)
plt.title("{}% Male, {}% Female".format(round(confidence[0]*100,4),round(confidence[1]*100,4)))
plt.axis('off')
plt.show()
```
![Gender Inference With Probabilities](/assets/images/cropped-face_gender-label.png)


## Are There More Male Faces of Data Scientists?

Not too surprisingly, yes, there are a lot more male faces in this data set. Out of the 158 human faces detected, 61.4% are classified as male.
{% include /charts/gender-mix-data-scientists.html %}

