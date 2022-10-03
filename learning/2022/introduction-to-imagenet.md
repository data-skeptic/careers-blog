# Introduction to ImageNet

It is a given that data drives research. As you would see, this saying played out finely with the ImageNet dataset. The ImageNet competition was arguably the most landmark event in the history of computer vision. It fueled the use of convolutional neural networks to achieve unprecedented results in image recognition and also, popularized the use of transfer learning to leverage already good models for different tasks.

This article will introduce what the ImageNet dataset was, how it came to be, and the achievements it has culminated over the years.

## What is the ImageNet Dataset?

ImageNet is a dataset containing 15 million images and 21,000 labels. The data labeling is so precise that it contains the breeds of dogs rather than generalizing all dog images to be dogs.

The idea of building such a repository of data was borne by Professor Fei-Fei Li, a computer science professor at the University of Illinois Urbana-Champaign, at the time. 

In 2006, after just becoming a Professor, Li observed that the performance of machine learning models by her colleagues was hinged on the algorithms used. In the same vein, the algorithms' performance depended on the size and quality of the data used for training. She imagined building a larger database of images, that map to popular objects. This would later be called the ImageNet dataset.

The first ImageNet dataset was published in 2009 as a poster at the CVPR (Computer Vision and Pattern Recognition) conference in Florida. At the time, people doubted the significance of Li’s work. Li’s breakthrough happened when she collaborated with the PASCAL challenge, a renowned image recognition competition in Europe, but with a smaller dataset (20 classes). The ImageNet dataset was eventually adopted for the image recognition competition.

## Where did the ImageNet data come from?

In a speech at [<ins>The Photographer’s Gallery</ins>](https://www.youtube.com/watch?v=Z7naK1uq1F8&ab_channel=ThePhotographers%27Gallery), Fei-Fei Li gave a rundown of how ImageNet was birthed. She emphasized the importance of cognitive neuroscience which resulted in the breakthrough computer scientists had with image recognition. Interesting findings from cognitive neuroscientists showed that humans did not have to think to identify natural objects. In other words, our brain does not do many (if any) physical activities to identify a tiger or a tree, but it does when identifying a sentence.

At the beginning of her research in the early 2000s, computer vision researchers had very little or no data to work with. Li initially was working on a kind of learning called one-shot learning. This involved training an image recognizer on three to four images and making inferences from it. The models were generally not performing well.

Li however was positive computers could do better with more data. She discovered the WordNet dataset developed in the 1990s. The image dataset was like a dictionary that indexed images according to their relationship with each, rather than in alphabetical order. The WordNet data had over 155,000 words.

That sounded better but Li wanted more. Without funding and graduate assistants at her disposal, Li and a few colleagues set out to download hundreds of thousands of images from Google and Flickr. Undergraduates at Princeton were given the pictures to label at $10/hour, labeling about 200 images per day. It soon became apparent that that process was expensive, slow, and unsustainable. 

In 2007, a graduate student told Li about the possibility of using Amazon Mechanical Turk to label a larger amount of data. At the time, Amazon Mechanical Turk was a newly formed marketplace where companies could hire workers from around the globe to do small online tasks. Li eventually hired about 50,000 workers over the next two and half years from 167 countries to perform the image labeling tasks. After all was said and done, the dataset was published in 2009.  

  

## The ImageNet Challenge

Within a year, the ImageNet dataset was widely used to train and evaluate the performance of image recognition models. Li had partnered with the organizers of the PASCAL challenge to use the ImageNet dataset to train and evaluate the performance of image recognition models for the competition. The model with the lowest error rate was declared the winner for that year. This was called the ImageNet Large Scale Visual Recognition Challenge (ILSVRC) or the ImageNet competition for short. 

Competition aside, researchers observed that their model performed better in other image recognition tasks, when trained on the ImageNet dataset. Li’s ImageNet dataset soon became the benchmark for determining the performance of machine learning performance for image recognition tasks.

In 2010 — the first year of using ImageNet — the best model had an error rate of 28%. The following year, the error rate of the best model decreased to 26%. In 2012, Alex Krizhevsk, Ilya Sutskever, and Geoffrey Hinton developed the popular [<ins>AlexNet model</ins>](https://proceedings.neurips.cc/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf) which had an error rate of 16% — a whopping 38% improvement from the previous year.  AlexNet, and by extension, the ImageNet dataset showed the revolutionary power of deep neural networks particularly convets for image recognition tasks. Today, the AlexNet paper is widely described as a major turning point in artificial intelligence history.

In the coming years, virtually all entries in the competition adopted the use of convets, tweaking AlexNet’s architecture and achieving slightly better results. By 2017, only 8 years since the commencement of the competition, the error rate went down to 2%. The competition was called off at that point, having beaten the error rate of humans which stood at 5%. 

  

## Improvement on ImageNet

Like every other technology, ImageNet has had its downsides. One prominent issue with it was its bias. Since the dataset was primarily picked up from Turkers on Amazon Mechanical Turker, the labeling is prone to existential bias that exists within those groups of people. There could also be bias in the images themselves since they were scrapped using search engines. [<ins>Research</ins>](https://sh-tsang.medium.com/review-stylized-imagenet-imagenet-trained-cnns-are-biased-towards-texture-increasing-shape-be4986004de) has also shown that ImageNet-trained models had a significant bias towards shapes than textures of images.

Bias is a long-term challenge of artificial intelligence with palpable effects. Amazon, Google, Apple, and IBM had [<ins>experienced the horrors of bias</ins>](https://www.nytimes.com/2020/03/23/technology/speech-recognition-bias-apple-amazon-google.html) when their smart assistant could not effectively communicate with users who were black because they were primarily trained on upper-class American voices.

But bias was not the only challenge with ImageNet. There are also concerns about copyright infringement, privacy intrusion, and obscene image content. This spurred the need to improve the ImageNet dataset.

One improvement is called the PASS (Pictures without humans for Self-Supervision) dataset. The authors of PASS in their [<ins>paper</ins>](https://arxiv.org/pdf/2109.13228.pdf), ensured the following to eliminate the issues with ImageNet.

1.  The dataset had no labels. This way there would not be search engine bias.
    
2.  They ensured the images did not contain humans to ensure they are not encroaching on people’s privacy.
    
3.  They meticulously filtered personal information or explicit content.
    
4.  The images used were CC-BY licensed. 
    

There are also [<ins>datasets</ins>](https://sh-tsang.medium.com/review-stylized-imagenet-imagenet-trained-cnns-are-biased-towards-texture-increasing-shape-be4986004de) such as the Stylised Images (otherwise called SIN) that replaces the texture of ImageNet images with paintings to eliminate the shape-texture bias.

Andrei Barbu, in one of our episodes, discussed [<ins>ObjectNet</ins>](https://dataskeptic.com/blog/episodes/2020/objectnet), another form of ImageNet. ObjectNet attempts to rectify the bias issues with ImageNet by using images that an autonomous machine is more likely to encounter in the real world.

  

## Where to from here?

Without a doubt, ImageNet sparked new possibilities in computer vision. If ImageNet taught us one thing, it is to reiterate that data fuels research. Today, tech giants such as Google, Amazon, Facebook, etc have created their own datasets to store images, voice clips, video snippets, texts, and so on. [<ins>EgoCom</ins>](https://github.com/facebookresearch/EgoCom-Dataset) is one of the projects by Facebook that uses data (text, video, audio) from humans to train machine learning models. The goal is to build a robust conversational AI. EgoCom is called the ImageNet of Conversational AI. Maybe this one would pass the Turing Test. Time will tell.