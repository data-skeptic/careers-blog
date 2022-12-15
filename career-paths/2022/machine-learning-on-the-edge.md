# Machine Learning on the Edge

Deploying a machine learning model to production is the machine learning engineer’s ultimate goal. There are however different ways to go about it. Machine learning models can be deployed on the cloud as a web service. For instance, a model hosted on a web service provider using Flask or Django. Asides that, the model can be deployed for batch prediction using Prefect or Airflow. Also, machine learning models can be deployed on edge devices such as Arduino boards, and Raspberry pi for a variety of tasks. 

In this article, we will focus on deploying machine learning models on edge devices. We will discuss what Edge AI is about, the benefits of ML on the edge, and the available options for machine learning models on edge devices.


## What is Edge AI About?

Edge AI is a type of AI that involves locally deploying machine learning models on physical devices rather than the cloud. This is the technology used in our mobile phones for face recognition, and object detection in smart cameras. 

In these applications, the ML-powered device does not need to be connected to the internet before it performs its designed task. 

Edge AI is also used in self-driving cars to make ML-driven decisions in real time. Drones use technology to navigate their way autonomously. Surveillance cameras use this technology for real-time video processing and object detection. 


## How does Edge AI work?

Edge AI follows the typical phases of developing a  machine learning model — the training phase and the inference phase. The training phase in Edge AI is quite similar to the traditional method. The model is trained on a large dataset to learn hidden patterns until it can make accurate predictions. In the inference phase, however, things change slightly from the traditional method.

Because Edge AI is usually specific to a use case, the model is typically ‘streamlined’ to yank off less relevant features. This is called pruning. Pruning allows the model to be lightweight, yet optimized for its specific use case. It should be noted that there is always a tradeoff between the accuracy achieved by larger-sized models and the limits of the hardware available on an edge device. While the smaller-sized model on the edge can be optimized to perform its specific task, it may not achieve the level of accuracy of the larger model. 

After the pruning and optimization, the model is deployed on a physical hardware device. Putting it simply, the ML model lives in the physical hardware (called edge), enabling the hardware to exploit the machine learning model autonomously and without connectivity.


## Benefits of Deploying Machine Learning Models on the Edge



### 1. Privacy

When dealing with sensitive data such as data medical imaging scans, images from surveillance cameras, audio from smart speakers, etc, privacy is paramount. AI on edge devices have better data privacy since the data is not transmitted on the cloud for ML processing. While a hacker can still compromise the edge devices, the chances of a successful privacy breach are significantly reduced.



### 2. Latency

Apart from securing the data, machine learning on the edge also has low latency. Since the data is not transmitted to the cloud whose server can be in a distant location, data transfer is usually faster and closer to real-time. This real-time processing is useful in machine learning applications that require quick response time. For instance, a self-driving car needs to respond to an emergency as quickly as possible.



### 3. Does not require connectivity

Imagine not being able to unlock your phone with face recognition because you lost internet connection. That would have been the situation if the face recognition technology was deployed on the cloud. However, because it was deployed on a physical device, you can utilize the feature without connectivity to a server. 

Since Edge AI does not transmit data, it does not require an internet connection. Inference does not need connectivity.


## How to Deploy Machine Learning Models on the Edge

Here are the three popular options for deploying machine learning models on the edge.



### 1. Google’s Tensorflow Lite

Tensorflow Lite is an open-source tool that enables machine learning on edge applications. It allows developers to deploy their machine learning models on mobile, embedded devices, and microcontrollers. This is what powers smart devices and many IoT devices to act intelligently.

Tensorflow Lite models can be of two types: with or without metadata data. A model with metadata has an additional description of the model in human-readable language with the one without does not have an additional description.

Tensorflow Lite models can be built in three different ways. First, there is a repository of ready-to-use models. Developers can deploy these off-the-shelf models for their specific use cases. Depending on the maintainers of the model, this type may or may not have metadata. Secondly, you can use [Tensorflow Lite Model Maker](https://www.tensorflow.org/lite/models/modify/model_maker) to train a model from scratch with your specific data. This type of model has metadata by default. Lastly, you can convert a Tensorflow or Keras model into a TensorFlow Lite model. However, these models do not have metadata. After defining the Tensorflow Lite model, the next step deploys it on the edge. Because edge devices are lightweight (i.e, they have lower memory), it is advisable to perform some optimization before deployment.

Optimization can be done using two ways: quantization and pruning. By quantization, the model’s parameters are reduced to fewer numbers, appreciably reducing the model’s size and increasing computation time. Pruning on the hand means cutting off the model’s weights that are less relevant for its application. The model still maintains its accuracy for its use case, while being able to be compressed to a smaller download size. Having got the optimized Tensorflow Lite model, you can deploy and make inferences on the device. 

Tensorflow Lite is perhaps the most popular tool for deploying ML models on the edge. It supports deployment to Android and iOS devices, Arduinos, Raspberry Pi,  Edge TPU, Coral Devices, and microcontrollers. The [Tensorflow Lite Interpreter API](https://www.tensorflow.org/lite/guide/inference) is used in the inference stage and supports languages such as Python, Java, Objective-C, C++, and Swift for models without metadata. For models with meta-data, the [Tensorflow Lite Task Library](https://www.tensorflow.org/lite/inference_with_metadata/task_library/overview) can be used.



### 2. Azure Stack Edge

Azure Stack Edge is another option to deploy machine learning on the Edge. [Azure Stack Edge](https://learn.microsoft.com/en-us/azure/architecture/hybrid/deploy-ai-ml-azure-stack-edge) devices are physical hardware where on-premise machine learning models can operate. However, the pipeline of working with Stack Edge devices is tightly-knitted to the Microsoft Azure cloud solution. The training data needs to be stored in Azure Blob storage. The data is also trained using Azure Machine Learning. Furthermore, the models are containerized and stored as docker files in Azure Container Registry. Having built this architecture on Azure, the model can then be deployed on the edge device — Azure Stack Edge.

The edge device can also get more sample data while in production and use the Azure ML pipeline to retrain the model for better inferences.



### 3. Amazon Sagemaker Edge

Amazon Sagemaker Edge can be used to optimize and deploy machine learning models trained on XGBoost, Tensorflow, PyTorch, and MXNET on edge devices. Like in the Azure Stack Edge, you can also capture more data from the device and retrain the model while the model is in production. Amazon Sagemaker Edge supports the deployment of models to any edge device including Raspberry Pi, and Arduino.

During deployment, Sagemaker Edge Compiler claims to automatically perform some optimization techniques on the model, making the execution time on the hardware 25x faster. One thing to note, however, is that the [Amazon Sagemaker Edge](https://aws.amazon.com/sagemaker/edge/?sagemaker-data-wrangler-whats-new.sort-by=item.additionalFields.postDateTime&sagemaker-data-wrangler-whats-new.sort-order=desc) is not free to use. 


## Edge Devices Made for Machine Learning

Due increased popularity of edge devices, companies are beginning to produce hardware specially designed for machine learning models. Some of them include:



### 1. NVIDIA Jetson

NVIDIA Jetson is a powerful GPU-accelerated computing hardware. There are three Jetson series with different specifications. They include Jetson Orin, Jetson Xavier, and Jetson Nano. Although the modules are in levels, Jetson hardwares are generally top performers for AI applications.



### 2. Google Coral

Coral is a small computing device used for powering custom-AI capabilities offline. It has a beautiful form factor with a relatively smaller size. With Coral, you also get to assess various models optimized for image classification, object detection, pose estimation, audio classification, and semantic segmentation. Nevertheless, you can still build your custom model to be deployed on Coral.



### 3. Intel Myriad Chips

Intel Movidius Myriad chip is a special neural compute engine, made for deep learning inferences. It was made to optimize machine learning processes, particularly image processing and computer vision applications. It has 16 programmable processors which enable parallel processing of computer vision computations. The processor is widely used in surveillance cameras, smart drones, AR/VR headsets, and so on.



### 4. AWS DeepLens

This is a deep learning-powered camera for developers. It allows developers to program the camera for their specific use case using machine learning models. There are also pre-trained models that can be used off the shelf. AWS DeepLens can perform tasks such as object detection, face detection, head pose detection, activity recognition, and so on. It runs on an Intel Atom processor with 8GB RAM and an Intel Gen9 Graphics engine. It may be a great alternative for quick computer visual applications.


## Conclusion

Machine learning on the edge is on an impressive trajectory for adoption. The industry is said to expect a [CAGR growth of 18.8%](https://www.alliedmarketresearch.com/edge-ai-hardware-market-A13111) between 2021 and 2030. If you wish to learn about running machine learning on small devices, the prospect is indeed huge. Hopefully, this article has given you some direction on how to get started.
