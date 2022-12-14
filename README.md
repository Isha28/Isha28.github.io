# Vision For Vision - Image to Speech Translation

#### Erik Pheng Kong Chang, Isha Padmanaban, Lakshmi Muraleedharan Nair (Dropped course)

### Links

<ul>
 <li><a href="https://github.com/Isha28/639-CV">Github Repository</a></li>
 <li><a href="https://docs.google.com/presentation/d/19177M2pjcrT509W3bB0UD_SGiLLfeW4iKsNmIHVUrs8/edit#slide=id.p">Presentation Slides</a></li>
 <li><a href="https://drive.google.com/file/d/1GzZdmT8tNiGnaFwRqif1GAU-ZawtdpSE/view?usp=sharing">Presentation Video</a></li>
</ul>

## Motivation

<p align="justify">The problem we are trying to solve is providing access to digital images for the visually impaired. In 2022, 2.2 billion people are reported to have a near or distance vision impairment. This means that many of them have limited access to the digital world as most of it is reliant on sight. One way that visually impaired people navigate the internet is through text to speech applications. However, this method does have its limitations because these simple text to speech solutions cannot read the text from images. Thus, we propose <strong>Image to Speech Translation</strong> solution which takes an input image and extracts text from it. The extracted text is translated to speech.</p>

<p align="justify">This problem is <strong>important</strong> because it allows visually challenged people to get a deeper enjoyment and utilization of the internet and perhaps help them navigate the outside world. Ultimately, this all allows them to be more autonomous in the real world and online.</p>

## Literature Review
### Image Pre-processing
<p align="justify">Low resolution, low contrast, high noise, and distortions are some challenges faced while retrieving text from images. The input images should be enhanced to obtain the exact text. One way of achieving this is by using computer vision OpenCV and Python libraries for Image Processing. Karun et. al. [3] explored the idea of extracting text from an image in a dynamic low light environment after eliminating noise. After capturing the input image, Fujii et al. [4] converted it to a gray scale image and then applied the required filtering with the help of Gaussian filter to reduce noise. We are incorporating image pre-processing steps such as thresholding and noise removal in our project to get accurate text from the image.</p>

### Image to Text
<p align="justify">Qi Zheng used segmentation algorithm to recognise characters with the help of multiple-size sliding sub-windows. After getting template images first, the SIFT features are extracted and matched with that of the template images. With this, multiple single-character-areas are found and are validated using a voting and geometric verification algorithm [7]. Text is extracted from images currently using OpenCV OCR. This OCR utilizes a deep learning model for text recognition that is highly accurate. But it requires the images to be captured in certain angles which is not ideal in real world. We are using Tesseract OCR for text extraction as it works effectively on different kinds of recognition such as images with words, text blocks and vertical text.</p>

### Text to Speech
<p align="justify">Yuxuan et al. [5] proposed a text-to-speech (TTS) model named Tacotron that is end-to-end and is capable of generating speech directly from characters. When text and its corresponding audio are given, the TTS model is trained completely from scratch to convert a new text file to audio. We are using open source TTS solution by Mozilla in our project for text-to-speech translation.</p>

## Proposed Solution
<p align="justify"> The solution to our proposed problem requires three main steps - Image Pre-processing, Image to Text with OCR, Text to Speech synthesis.</p>

### Step 1: Image Pre-processing
<p align="justify">Below are the important pre-processing techniques we applied on the input image to enhance the quality of the image and extract the right text. We are using the OpenCV python package for this purpose. This step will greatly improve user experience and eliminate some of the current limitations of the OCR systems.</p>
<ul>
  <li>Grayscale Conversion : We are using OpenCV cvtColor function to convert the colored image to grayscale image.</li>
  <li>Threshold and Binarization : This step converts the grayscale image into a binary image with only black and white color. This is done so that Tesseract OCR can identify text easily.</li> <!-- For every pixel, the same threshold value is applied. If the pixel value is smaller than the threshold, it is set to 0, otherwise it is set to a maximum value. -->
  <li>Noise Removal : We used openCV erode and dilate method to remove small white noises and increase the object area of the input image. We applied median blur filtering technique to preserve the edges of image while removing noise.</li>
</ul>

### Step 2: Image to Text
<p align="justify">We used open source Tesseract Optical Character Recognition engine for obtaining text from images [6]. This library is proven to provide better quality output. We provided the required configuration settings in a Python program to read through categories such as texts, numbers and special characters from images and output them with acceptable level of accuracy. This needed trial and error effort to find the right configuration for each of the categories. We have tested the code with rich set of images including images with short words, magazines, and handwritten notes to validate the correctness of the module.</p>

### Step 3: Text to Speech
<p align="justify">In this final step, the resulting text is sent to the text-to-speech solution. We used an open source TTS solution by Coqui, which is derived from the Mozilla TTS solution. This TTS solution is made up of three components, the TTS model itself, the dataset used, and the vocoder model. We used the pretrained TTS model known as Tacotron2 with Dynamic Convolutional Attention (Tacotron2 DCA). We then used the LJSpeech dataset, which is a public domain english speech dataset and for the vocoder model we chose the Multi-Band MelGAN because it was the fastest model.</p>

## Results

Below are some of the interesting results we have obtained. <br>

<table border="5" bordercolor="black" align="center">
    <tr>
        <th>Input Image</th>
        <th>OCR output</th>
        <th>TTS output</th>
        <th>Comments</th>
    </tr>
    <tr>
        <td><img src="handwritten1_preprocess.png" alt="" border=3 height=150 width=300></td>
        <td>This is a handwritten<br>example<br>Write as qooal as you can.</td>
        <td>
          <audio controls> 
            <source src="handwritten1_preprocess.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Handwritten text. Image <br>pre-processing is not done. <br>Tesseract output is not accurate.</td>
    </tr>
    <tr>
        <td><img src="handwritten1_preprocess.png" alt="" border=3 height=150 width=300></td>
        <td>This is a handwritten <br>example <br>Write as good as you can.</td>
        <td>
          <audio controls> 
            <source src="handwritten1_preprocess_res.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Handwritten text. Proposed <br>image pre-processing is applied. <br>Tesseract output is accurate. <br>Shows the importance of our <br>pre-processing techniques</td>
    </tr>
    <tr>
        <td><img src="print_preprocess.png" alt="" border=3 height=150 width=300></td>
        <td>This is a lot of 12 point text to test the<br>
          ocr code and see if it works on all types<br>
          of file format.<br>The quick brown dog jumped over the<br>
          lazy fox. The quick brown dog jumped<br>
          over the lazy fox. The quick brown dog<br>
          jumped over the lazy fox. The quick<br>
          brown dog jumped over the lazy fox.</td>
        <td>
	  <audio controls>
            <source src="print_preprocess.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Printed text</td>
    </tr>
    <tr>
        <td><img src="para.jpg" alt="" border=3 height=150 width=300></td>
        <td>???Health is wealth??? is a very famous<br>
        saying which means that where there is<br>
        health there is wealth. A healthy person<br>
        has the power to achieve everything in<br>
        life.<br>
        Being healthy and fit just doesn???t mean<br>
        being physical fitness but it the overall<br>
        fitness that is emotionally, socially, and<br>
        mentally. A healthy body destroys all the<br>
        negativity.</td>
	<td>
	 <audio controls>
            <source src="para.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Articles</td>
    </tr>
    <tr>
        <td><img src="menu.jpg" alt="" border=3 height=150 width=300></td>
        <td>FOOD ALLERGY NOTICE<br>
        If you have a food allergy or<br>
        a special dietary requirement<br>
        please inform a member of st<br>
        Thank You</td>
	<td>
         <audio controls>
            <source src="menu.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Real world signs</td>
    </tr>
    <tr>
        <td><img src="sign.jpg" alt="" border=3 height=150 width=300></td>
        <td>ROAD CLOSED</td>
	<td>
         <audio controls>
            <source src="sign.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Real world signs</td>
    </tr>
    <tr>
        <td><img src="handwritten2_preprocess.png" alt="" border=3 height=150 width=300></td>
        <td>How jo Quickly Turn<br>Your Own Handwriting<br>Into a Font</td>
	<td>
         <audio controls>
            <source src="handwritten2_preprocess.mp4" type="audio/mp4">
          </audio>
        </td>
        <td>Handwritten texts</td>
    </tr>
</table>

## Evaluation
<p align="justify">We evaluated the accuracy of text retrieved from image using recognition rate, and error rate. Our OCR model performance is evaluated by calculating Normalized Character Error Rate (CERNorm) and Word Error Rate (WER). These metrics show the extent to which our OCR module transcribed text and how the ground truth text differ from each other. CER and WER represent the number of character/word substitutions or deletions, or insertions needed to transform one word/sentence into another respectively. Both of these quantitative metric systems are based on the Levenshtein distance.</p><br>

<center><img src="formula1.png" alt="" border=3 height=50 width=100></center><br>
<center><img src="formula2.png" alt="" border=3 height=50 width=100></center><br>
 
where,
<ul>
 <li>S/Sw : Number of substitution of characters/words</li>
 <li>D/Dw : Number of deletion of characters/words</li>
 <li>I/Iw : Number of insertion of characters/words</li>
 <li>C : Number of correct characters in case of CER(Norm)</li>
 <li>Nw : Total number of words in the reference in case of WER</li>
</ul>

<p align="justify">We have considered a dataset of 200 images containing English letters in .jpg format with their equivalent text saved in .txt files to evaluate our solution. The dataset also contains difficult images, like images with high noise or blurriness. As we evaluated our solution over the dataset, we obtained a Normalized Character Error Rate score of 6.58% and Word Error Rate score of 18.91%. Our solution achieved an <strong>accuracy</strong> of around <strong>88.33%</strong> in terms of character recognition rate over the testing dataset. With our sample input data, we found that our image pre-processing techniques takes less time than OCR or TTS.</p>

<p align="justify">We have evaluated our text to speech solution. As we saw earlier in the results section the TTS was fairly accurate in reading the text. However, there were some discrepancies in the audio files. After some more testing we found that these audio files could be fixed simply by adding a period at the end of the sentence. <br>Here is the adjusted audio file for the food allergy text:<br>
     <audio controls>
          <source src="menu_fixed.mp4" type="audio/mp4"> 
     </audio>
     <br>
     <br>
Here is the adjusted audio file for the road sign text: <br>
     <audio controls>
	  <source src="sign_fixed.mp4" type="audio/mp4">
     </audio>
     <br>
     <br>
     This raises the question on what is truly wrong with the TTS solution, as it seems that it can handle most of the text that comes its way. Perhaps this problem could be solved by training our own models, but this problem may stem from a deeper issue caused by the source code. Furthermore, it seems that after some further testing the discrepancies seem to occur at random. For example, the TTS struggled with the singular words 'You' and 'Road', but after using these words in a sentence like 'How are you today' the discrepancy disappeared, regardless of the punctuation. Ultimately, further research is required in order to fully debug the TTS solution, but in its current state it is accurate enough for our purposes.
</p>

## Conclusion

<p align="justify">We have devised an end-to-end image to speech translation solution. In addition to the image pre-processing done in Tesseract OCR, we added further pre-processing techniques which improvised the text extracted from images as shown in the above results. This solution provides better results and recognition rate with handwritten texts/noisy images.</p>

## Future Work

<p align="justify">In this project, we have only considered the alpha-numeric data associated with the image. To extend this study, we can also consider the signs, symbols, diagrams associated with the image to generate speech to provide a complete information. Image pre-processing techniques can be enhanced further to reduce the obtained error rate while extracting text from image.</p> 

## References
<ol>
  <li><a href="https://github.com/coqui-ai/TTS">https://github.com/coqui-ai/TTS</a></li>
  <li>Ackland P, Resnikoff S, Bourne R. World blindness and visual impairment: despite many successes, the problem is growing. <em>Community Eye Health</em>, 2017.</li>
  <li>Karun Somasunder M, Amal J.S, Gopal Gopakumar, Suraj V Thomas, and Keerthi Krishnan. Text to speech conversion using google vision api. National Conference on Smart Systems and Technologies, 2021.</li>
  <li>Yasuhisa Fujii. Optical character recognition research at google. IEEE 7th Global Conference on Consumer Electronics (GCCE), 2018.</li>
  <li>Yuxuan Wang, RJ Skerry-Ryan, Daisy Stanton, Yonghui Wu, Ron J. Weiss, Navdeep Jaitly, Zongheng Yang, Ying Xiao, Zhifeng Chen, Samy Bengio???, Quoc Le, Yannis Agiomyrgiannakis, Rob Clark, and Rif A. Saurous. Tacotron: a fully end-toend text-to-speech synthesis model. arXiv preprint arXiv:1703.10135, 2017.</li>
  <li><a href="https://github.com/tesseract-ocr/tesseract">https://github.com/tesseract-ocr/tesseract</a></li>
  <li>Jian Zhang, Renhong Cheng, Kai Wang, Hong Zhao, ???Research on the text detection and extration from complex images???, Fourth International Conference on Emerging Intelligent Data and Web Technologies. Vol. 10, 2013, Page no. 708-713.</li>
</ol>
