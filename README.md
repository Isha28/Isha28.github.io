# Vision For Vision - Image to Speech Translation

#### Erik Pheng Kong Chang, Isha Padmanaban, Lakshmi Muraleedharan Nair

## The Problem

<p align="justify">The problem we are trying to solve is providing access to digital images for the visually impaired. In 2015, there was an estimated 253 million people world wide who are visually impaired. This means that many of them have limited access to the digital world as most of it is reliant on sight. One way that visually impaired people navigate the internet is through text to speech applications. However, this method does have its limitations because these simple text to speech solutions cannot read the text from images.</p>

<p align="justify">This problem is <strong>important</strong> because it allows visually challenged people to get a deeper enjoyment and utilization of the internet and perhaps help them navigate the outside world. Ultimately, this all allows them to be more autonomous in the real world and online.</p>

## Current Solutions
#### Image Pre-processing

#### Image to Text
Text is extracted from images currently using OpenCV OCR. This OCR utilizes a deep learning model for text recognition that is highly accurate. But it requires the images to be captured in certain angles which is not ideal in real world.

#### Text to Speech


## Proposed Solution
#### Step 1: Image Pre-processing
<p align="justify">Below are the important pre-processing techniques we applied on the input image. We are using the OpenCV python package for this purpose.
<ul>
  <li><strong>Grayscale Conversion:</strong>We are using OpenCV cvtColor function to convert the colored image to grayscale image.</li>
  <li><strong>Threshold and Binarization:</strong>This step converts the grayscale image into a binary image with only black and white color. This is done so that Tesseract OCR can identify text easily.</li> <!-- For every pixel, the same threshold value is applied. If the pixel value is smaller than the threshold, it is set to 0, otherwise it is set to a maximum value. -->
  <li><strong>Noise Removal:</strong>.</li>
</ul>

#### Step 2: Image to Text
<p align="justify">We used open source Tesseract Optical Character Recognition engine for obtaining text from images. This library is proven to provide better quality output. We provided the required configuration settings in a Python program to read through categories such as texts, numbers and special characters from images and output them with acceptable level of accuracy. This needed trial and error effort to find the right configuration for each of the categories. We are tested the code with rich set of images including images with short words, magazines, and handwritten notes to validate the correctness of the module.</p>

#### Step 3: Text to Speech
<p align="justify">In this final step, the resulting text is sent to the text-to-speech solution. We used an open source TTS solution by Coqui, which is derived from the Mozilla TTS solution. This TTS solution is made up of three components, the TTS model itself, the dataset used, and the vocoder model. We used the pretrained TTS model known as Tacotron2 with Dynamic Convolutional Attention (Tacotron2 DCA). We then used the LJSpeech dataset, which is a public domain english speech dataset and for the vocoder model we chose the Multi-Band MelGAN because it was the fastest model.</p>

## Results

## Sources
<p align="justify">https://github.com/coqui-ai/TTS</p>
<p align="justify">Ackland P, Resnikoff S, Bourne R. World blindness and visual impairment: despite many successes, the problem is growing. <em>Community Eye Health</em>, 2017.</p>
