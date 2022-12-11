# Vision For Vision - Image to Speech Translation

#### Erik Pheng Kong Chang, Isha Padmanaban, Lakshmi Muraleedharan Nair

## The Problem

<p align="justify">The problem we are trying to solve is providing access to digital images for the visually impaired. In 2015, there was an estimated 253 million people world wide who are visually impaired. This means that many of them have limited access to the digital world as most of it is reliant on sight. One way that visually impaired people navigate the internet is through text to speech applications. However, this method does have its limitations because these simple text to speech solutions cannot read the text from images.</p>

<p align="justify">This problem is important because it allows visually challenged people to get a deeper enjoyment and utilization of the internet and perhaps help them navigate the outside world. Ultimately, this all allows them to be more autonomous in the real world and online.</p>

## Current Solutions

## Proposed Solution
#### Step 1: Image Processing

#### Step 2: Image to Text

#### Step 3: Text to Speech
<p align="justify">In this final step, the resulting text is sent to the text-to-speech solution. We used an open source TTS solution by Coqui, which is derived from the Mozilla TTS solution. This TTS solution is made up of three components, the TTS model itself, the dataset used, and the vocoder model. We used the pretrained TTS model known as Tacotron2 with Dynamic Convolutional Attention (Tacotron2 DCA). We then used the LJSpeech dataset, which is a public domain english speech dataset and for the vocoder model we chose the Multi-Band MelGAN because it was the fastest model.</p>
## Results

## Sources
<p align="justify">https://github.com/coqui-ai/TTS</p>
<p align="justify">Ackland P, Resnikoff S, Bourne R. World blindness and visual impairment: despite many successes, the problem is growing. *Community Eye Health*, 2017.</p>
