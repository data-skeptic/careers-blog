# AI for Text-to-Image Generation

While machine learning algorithms were doing great with tabular data, understanding texts was a completely new challenge. Human language is complex, with numerous contextual meanings. Adding images to the mix makes it even more complicated. 

In the past decade, there have been several breakthroughs in natural language processing and computer vision. Google Translate translates texts from one language to another almost perfectly. Your phone’s lock can recognize your face in a split second. The autocomplete feature on keyboards now works as though it reads our minds. Medical imaging is becoming as good as expert radiographers. We communicate with Siri seamlessly. Self-driven cars are now flooding our roads. The list goes on and on.

While the progress in AI has been enormous across different fields, generating images from text is perhaps one thing that would remain mind-blowing. In this article, we will give a background to generative image technology and discuss some popular text-to-image generation tools. We’d also try out the tools ourselves and see their results.

## How Generative Image Models Came About

The idea of creating generative image models was fueled by image captioning. In image captioning, the machine learning model looks at an image and describes the scene in words. In other words, it converts texts to images. An image captioning model is trained by an incremental classifier. It classifies objects in the image, actions perceived, objects in the background and foreground, etc, one at a time. In short, incremental learning works by the principle that everything we do can be broken down into individual tasks. Thus, it attempts to find how to solve each task and then efficiently piece it all together incrementally.

For instance, in the image below, an image captioning model can first classify the objects (females), then their outfit (sportswear) then the background (an open space). Merging these can suggest that there are two female athletes in an open space. 

Next, the model classifies their actions. Classifying their hand gesture, the shape of their mouths, and eye contact accurately would suggest that they are communicating. Finally, classifying their posture would suggest that they are sitting. 

![](https://lh6.googleusercontent.com/9IbdNun54OuCYc-_uwlm1G3r66PDun7Nvg3wiuaelyW7vjK7gXyV5cWAcIObw5qeS7NUxzAPo1zb2NmWHP1Ot5DqmbZnhUTumBWZlBnUqbUBqTo24HYc9xH9f5Et-n_lqwAPxrVlj-OQbo7G9HqEMYmuYiXIkLRv0SNiED7Dt01MR6g1nF0SJHxj2A)

Photo by [<ins>Andrea Tummons</ins>](https://unsplash.com/@krewellah87?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [<ins>Unsplash</ins>](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

The first and second learning can spit out the caption, “Two female athletes talking”. Adding the third learning can spit out the caption, “Two female athletes sitting and talking in an open space”. This is how incremental learning works for image captioning.

## Behind the scenes of Generative Image Models

As image captioning grew, researchers tried to see if they could reverse the operation. This time, turning texts into images. A breakthrough in the text-to-image space happened when OpenAI announced DALL-E on January 5, 2021. In April 2022, they announced DALLE-E 2. DALL-E works using two major technologies: CLIP (Contrastive Language-Image Pre-training) and Diffusion. 

CLIP serves as the interface between text to image. It is trained to not just identify objects in an image but to predict the most appropriate caption to an image from a list of random captions. CLIP was trained on 400 million image-text pairs of data. After training, it creates a vector space of images and texts, where similar images and texts are placed close to each other. The fact that it was trained on both text and image gives CLIP room for zero-shot learning, meaning it can classify images that were not present in the training dataset but only appeared in the test dataset.

The second most important technology to DALL-E is diffusion. Diffusion is the process of training a model to scramble pixels of an image and then correcting the scrambled pixels, one step at a time, to form the initial image. By training the model to create an image from noise (the scrambled pixels), it can create a good image from randomness using the text-image vector space from CLIP. Based on the text, it changes the pixels of a random initial image, one step at a time, until the image sufficiently captures the meaning of the text.

DALL-E is currently not released to the public. However, in June 2022, they announced a beta version with millions of people already on the waiting list.

## Mid Journey

Like DALL-E, Mid Journey is an image generative model that creates realistic images and paintings from texts. Only that Mid Journey is available for public consumption. It was developed by a team of self-funded researchers that sought to expand the imaginative powers of humans using AI. 

I signed up to test Mid Journey on their Discord server. Meanwhile, you can do the same by opening a Discord account if you do not have one and following the instructions [<ins>here</ins>](https://midjourney.gitbook.io/docs/).

To try out Mid Journey, my first prompt was: A schoolboy riding his bike without his shoes

![](https://lh3.googleusercontent.com/0sLOxXf6p-WWoKO0NuDThZiUPKVvnG8m8sKZrNHa37EW42soXo9C21XsazQX69I8Ui17idgMV7IXcGjYrC-N52JoAeJdKIldQHk-IHOmH0NGrurPHVJL-hsr_MO_BbZPOQMI_JRYYdNrMeFl-tJF5pGQWJcBPp26IVz6AmTmAKYVgDf16capHl-Ysw)

![](https://lh4.googleusercontent.com/_kW8tVP9ozV97Kk7gPEFZx-LeXeaRjgh1d2rCH7GYQoKXZ96xoadV-9mh5AkUtFJJp-KTwvLg7ZmsbmcGmvBWj56qaQlxyQsOkItlEe4EXvix_WGAq4ltVfKA6BLDgdQ2K0-ADJ0aQxyhFr41pm981MULYXaEiEaYEfrVL_E-MI8Lf8ZXZ3Ik6ux7w)

![](https://lh3.googleusercontent.com/bJai_rAdVZMk9ECXUMtbn8qcF_52j0tWQFoPoFHGf97FoVsSCM8qLjjukJ6AJCg_rh-ZJWuyW1VCIp8k5azZv6rfqdSO8vdJPVGb4mXiumN6q27R-Axv-T2JjuFXsaFVaPZ6e2xHxffdsZ17bTqDZR_DNm0HcCyuoXNOH44t41BE24nzMVU40RCsJA)

![](https://lh3.googleusercontent.com/NcuxUPpGc3ElflZtW55kmjRzyKwVaDJk9h1BUR6hedEg6CaBaazRGvCMuPUfzanJ-wMHS8NHefdMoj7L2HcRoj-75xdXLqAGXNoqG1GXUVOUQwNo9J3svZosdAXMKgnEzE2fLvStM1to7U_nT7i9RueGHr_xPbDraHmUqhiHBvxiR8cCKPFbpMa4Yg)

The goal was to test if Mid Journey can capture the key objects in the text in the generated image. It did. We see the boy wearing a school bag, indicating that he is a schoolboy. In all the results, the boy was with a bike. But for some reason, I do not see the boy barefooted. I do not also see the boy wearing shoes. His feet region was quite unclear in the paintings. It would appear that while the Mid Journey was clear on not showing shoes, it was not sure whether to show him barefooted.

To confirm my guess, my next prompt was: a schoolboy riding his bike barefoot.

![](https://lh5.googleusercontent.com/j3tC0h5h_cBUsAHTuA276xkl2IFiqJoxnZN3URAYwwC_elJBONlo4-LRK8ocQAmaTs9DpfJ_C5X2P2C_HLzSU_jYyJ9Zi_JnySfWcBNDDnRTVnwpfvInWYb9Nz_jRs0ffaUaDka3oQem0RJDe1NjfeSm7vB8mS1Dly45kue7I-NMCFwAi48ZCohHEg)

![](https://lh4.googleusercontent.com/wHysSxGY33JLRNrapVivKJ_HqfA7xEsLT7haonGItEmFBD0zdDGI5Jtu1X4PnWxG2rglEECT67YJu1X951XZ1s8_pAqiuRlU2Tu6gK7Ge7fnGa7r0DKcU9i9bOZOZsByZ5QXxbjnJH-xL3h8ke2EY1Ux6322fdP40Jyk-OmDz4EmAzt8tqYGEXs7XQ)

![](https://lh5.googleusercontent.com/2jFh2vXbFmWbmUzuY6jklvvBsVpJEbh_J_Y3a5fKq6CTQa-LPM5PPHq6vk0XbCQq4mkBMDw2COkDq4XPiM1zcOkyQGPCmELsUNiLmtOEeSnQ09lQEp684dniQkki8B2fEsYE5NJbkjQGJ12LQXG7oL6aqf9BV6zhR8u_O2Kmfg_S75Y8hkv2xizINw)

![](https://lh6.googleusercontent.com/oAga5ryx-ficfIpQkZwF-aPMbXPndqBLauiB47YM1IPb_qqDEm9WWe4wQ2vkUd7eXZIJeMzfEpi6xw2OyqrDPmkEfJ3X94Ztwzx1XqL780hFpmWkbxu1UJwPNTMhTWfIzQCzPuh0o0mq4-2aRqGRwwogW897ABRQ9emuGRXjx4mUO-8Ttvh64apglw)

Here, his feet already were a bit clearer, and it was more obvious he was not wearing shoes.

Next, I tried something weird. My prompt was: a dog in a tiger’s body.

![](https://lh5.googleusercontent.com/E9N2ZyUf277Reet44N4Qf98DZExbJ4iXv_lL6V52jgNvVUrTQFCP-QsDpc9xiWcEj7njy4266dVj5zXO2HMWmBSBKBhUmbuNj4-Gu4SSVTQrIMAw_vGTXomE3hzFgYzynroxwHyi8KNi_TTuOIURPV_Ne1HSuTDLC6C8LGzJIn3iGyPRg72OiMXvJA)

![](https://lh6.googleusercontent.com/tnh2BeGZhV4vjDWFyxoK6kLZRaU6kHqh0cwBFJuIAxXjJWTH75mOOXDc5A5vAM2x6MccBrsX75gple2-yGq3AiRUebWGhySvzKsj4RsjdaDgveHtu4P03F5ibavdidYDnk-H-cGZ-HZkipy88Ru1rEG0c9InAJgm7UWaXlVm4yisWzFC5XF9uXvuFA)

![](https://lh4.googleusercontent.com/YP8L8nus59NZrFPkmEll15bv7NxSFZefse4J2JORHwFHLMfmHlHrzJfU8ARluAwelswJDC8mXrCzDnf7WtHJUim4Uw5e8SlqLVyrNgiCEMmaQEHU0UFpNSDtKAGSJVcKGsTLu9X1PcgRlbNqeS7wffj3VfbpILmvSFFnrGMW4wNIbQJrsm_ZyBuT3w)

![](https://lh5.googleusercontent.com/R-8-NLHUI8eEeli58C4CR3_wYMkkZ59nP_PeDZdCnlgKhklYKrAi9hE_DsUAOEomBj1Umw4f9TAiT1h4DsBc_0ARDzvSwD6J506CGozU5WhLMooxea7qHccAqpZa5tPrHPjcTsNC5D_8HfHt0fYy-BMKSWn5_t9SBPHgdeXyrOl4JcyOZEv_SYIaGg)

Here, the model ensured all images had a dog face but had stripped skin (mimicking the body of a tiger). 

Next, I tried something even weirder. The prompt was: a party on the moon.

![](https://lh5.googleusercontent.com/2SBOn7v6Ynkd08m18RKTqYh4H6vnyGqYOi_HmdPwKkEOVf5ZZfYSYV9V1G4nLJGmoDRMaK8o2Z2sBIPPoOxNEAhrI15PDqOPEVtdKttXE5qZahpfnAPQ9JXNnRdNGFcpo6naRVAcFgKGwOxQFj2Rm8RbOVQxmKkfG93fUNSBNU6AxhQQ4yoj7kVh9g)

![](https://lh6.googleusercontent.com/K-UO3N9jFF7A1G_xb_lwKg8S7VqieKPgcUGTBkzTsH4iKU5PvEYtt_vVL9oAX_kXY3H2avgxmEu-Fswivn2RoKK9QMWHibTBX8JajmqXEh7B_2kVtXBVs4y5iMJ_nrNwOPdJAjH8iMwulDv5SLsGaw8sB1Hr5zRiM5mcfPomrURgKo9hXJze_VEssw)

![](https://lh6.googleusercontent.com/mQ_F4QZ2POWX5bZdoFbA2MNXqJoFp2w1LwLCJSSO6VzInfBEVJ6WG5kU8KXKK51VkoaHvZOldiINyCNvgs-MSMHrzjn3lcfpiHB2yQiE1nKe_5u3eGkoxjV_KY0iMUVA_gNyIL4jaUSc_slLXMGNphxp78FMpzaZb5SuFRUni4ogkzBMK69qaCt8mA)

![](https://lh3.googleusercontent.com/FNPC6svAEUw-Dw5KUBySSKuQxMrQJZfNQ5D_tdPhbGHQzN4F-n0XYPjHYFdVvZPenEBz7CnyQYsyAfM_IEBpkW3oIh74VflJWt96Up6cjUQK0buyskcdIOzl9irJwYSwk-VMNyHsq-CUV6C1gMGZFd0MW_3vkqPsEbG16ixAP8uYwOzmxAbRt8flZw)

This result is quite tricky. In the first two, the image depicts some bubbly activities inside the moon, indicating a party on the moon. In the last two, however, it was more of a party on earth with full moonlight. Apparently, Mid Journey still struggles with some imaginative thoughts.

I tried to imagine something more. My next prompt was: the world in 1 million years.

![](https://lh3.googleusercontent.com/rYKFGqHGbZqcrQ4i7ah3UDIxOPaNCcy8jFEmkDLfViPlXkuzYXWAsL-i-H-2T-3cXzr_M-sRYmY0Kc_bohHGHK-mE4POngkD35PxnuX1YEbHuPDA_5gWxYM_boHt0If1dBuH3CANO64NsG4cjmZZnUPcxQTphp4jRiyPygMmOYVmgHmdAdONtnxi3Q)

![](https://lh4.googleusercontent.com/ClBQSoUwrfvM5pW45JjWwIaYd-WuyVK7sBk_dto9FVy7ftNrIWC-ofnhjNcd-lkdM6qPT5dToXUlC_ecMUEUDGUR4RVQDBoUBl-WZ2cMje0NK_VLW8j3N-sQi_5uoB-QeasGkUXbnveyudpPZCkPHN8voP-UwLTeFBCPUeC6THsqvQ3ADjBctBBaiw)

![](https://lh6.googleusercontent.com/fh6vYnUMkRR1-X7hoA4hfbMlEa9_xOBFXuiwnGzJfY1pxFNN8QFbrUxweoRJdzYibi9TAM517oblILnhXjci_N4ZH-Ep0WZv6foSeXT8CVGUMSFgJYUGk__lw_zGM04HOcE7Na3XTSX3OXkOBQNUwTtM99gHK7UQ4A0HhFFGhnXq8uEteWWIrWW__Q)

![](https://lh4.googleusercontent.com/vxBO7x-67ufQd4O6vCbt2OduKaO7P3eLA1yZNOIkdRYxmu_nbLIrPSzjSP_ci0sDIfgqWl6KwRr6uTuft8bPKqhFrUq9DSc8c7LbxhkF3Q0ZpogTUP8gbCn79qKnuJJW-Qx8Lfop_SKrGj7wklYahFJvrvOUjnI66xkneAvvcrcNHfJc1SCNzHavwQ)

I’m not sure if these images mean there’d be an apocalypse at some point but here you have it.

Finally, I tried one more weird prompt. I typed a computer that can read the mind.

![](https://lh4.googleusercontent.com/f2clCoS8TkJXNmG8tpXMFjDH5PWUXOsAsA6d1Wsf6StH968NCIe7hyY5-1hMjATWS7phXjTC0CZxUgZi1EMLF6q6wrTY1lApEX07zNFTyOt4lGG4j_ket-hK2t1fL1FksnT5t2vm-YzCdmKhk6JeKbMLcVHllKQpCE36bJoTHt1BB7N7m7DYeuD6Nw)

![](https://lh3.googleusercontent.com/3lMCl280w3uxCBofRo_6ZIQ0C9Z8G2P631KalgEneYUVgV9hLjj9dF7E3zXehfH7rclX0lDOV7w0hQi9cHAGza1Gv_CYz3Nzn-b01kru2CA5nmJIwZ3sARqOoKnstQq3OqSnlVpXz5T0atCUeyUqSzeqi_K2tpv9mTNkDuCQ3rR0znlMvzUIYzRimQ)

  

![](https://lh6.googleusercontent.com/JwlAyja-xvIfJ0N4OOT9wv1SzYPwSNZmtmJOQ_b2L_SVZdaoloPJEtqpZ_aFb0FKu700YpFMXX0rliMDhn1X2MaXyZ72iuVLjAaAqDOtsE6zYvpGDYQnS3UKldQjtk5RR1z-UhPiM4Rju18-raIPdkx_OiI_2f62ioSSarjyMTtZEpHjWAeZnPXZ6g)

![](https://lh6.googleusercontent.com/KgH7DWEN5VijFjHl2n316NenOM1W9bLf2x1QbeE1UkqdhgrCsch7ouOayR2tQzMi0xLoOdySdSP9EA2317JPfYG7uqzyX4JUXwTyGPqgLRhuT1ypxCLv6D8y88Ohofj8GMOJTtWYpmPmg0J7CQdw8T8osZloBU3OW_5DOTHycCR4wQ2vq3PiSLR_Pw)

Of course, we do not know what the mind is and cannot represent it in an image. However, we see Mid Journey differentiating this computer from others with the fading red screen on a blue background. In the second and third frames, we also see a book, perhaps representing the word ‘read’.

  

## Other Tools for Text to Image Generation

### 1.  DALL-E mini
    

As mentioned earlier, DALL-E is currently not available to the public. However, there is an open-source model that stemmed from DALL-E and can be used for text-to-image generation. This is a project by Craiyon and can be assessed on [<ins>HuggingFace website</ins>](https://huggingface.co/spaces/dalle-mini/dalle-mini). 

Now let’s try out DALL-E mini. The first prompt was: a boy riding a bicycle.

![](https://lh5.googleusercontent.com/mzpC5cKWev4oU6qsSEOg_nlB0S8b03iDbgePmWSWI5YkxqcEDiQpDcTz1TvqnzEeadTxRBsoOpQx6G__sJ4xr6CCr_8TvAeKuJrClSVmAakBwqZxMOhXD5hffkimoxov1V3e04nxe8obHMzkzvf9JWeizFDG78dbbTFNQ9WBJI_VWtGnM58Rm_NSog)

Aside from the face of the boy, the images looked nice in my opinion.

Next, I tried out, ‘a party on the moon’.

![](https://lh5.googleusercontent.com/jf0M7wN3wdycz03L16eQOPyb1UwzY2qfkVKQIgRQH_xstW3QmC0NgsR0qNi_h-A3Z6F55y6EWoNbd2ZVdfzUUPCSMWxwKP6IWqUjdYJw5YSmWilVYZAi3gVo9d5ACtQ9q2t9QuiO8YoZjIxKotaMhMa9JGP7UFCuiBYzaueY59zPk1d0KuCh-O4Bxw)

Some of the images looked unrealistic but they sure attempted to capture a party happening on the moon except in the 6th and 9th frames.

  

### 2.  NightCafe
    

Night Cafe uses AI to create paintings from texts. It harnesses the power of VQGAN (Vector Quantized Generative Adversarial Network), an adversarial neural network, and CLIP to create images from a list of trained image data.

I tried my hands on Night Cafe to see the image it produced. With the prompt, a schoolboy riding a bicycle, I got the image below.

![](https://lh6.googleusercontent.com/1jT4IiIlH0Ab8rOX0GI8Z9SSNEqkGpGvbpKkC5SkpaXnmQ_yGN9MM30JUu_yQU0v7-xv126RPQU6K3eYHRw5qYcbX-qiyvbXfFctodSojKO6Z-qog9-pHOCC0tjbs0UfA1ebyk8oi7q2jY4czDB24APUab0UMNakMPWqKEbPbchyE_7PxO1g9JMP5g)

I also tried ‘a party on the moon’. Here is the result.

![](https://lh4.googleusercontent.com/V9JhIX9a2DK3D5qg_xXBQw45eX_87-zI0FvlvaOiDfGxM6v_5MFdBJGHs2kgUh46nB6E90uOHFrKHPBwbubZzFUQmq-OOoygE0TOfuew2IlmQ8YKXGb8B7hlb8j8GTYF0K6F81u4j4VlK4Awk__KZItgc6TQlJ4NTPifqhcn0l-geko4Zn07wPPMVQ)

I find this more realistic, but not aesthetically pleasing. We see people in spacesuits popping wine. Quite a party!

  

### 3.  StarryAI
    

StarryAI is another image generation tool that uses a customized form of VQGAN-CLIP combination called Altair, and a CLIP-guided diffusion technology called Orion. On StarryAI, you can upload an initial image to create your desired artwork. This is an optional step as StarryAI would create the image from noise, if you do not upload an initial image. 

To test how StarryAI performs, I entered the same input: a school boy riding his bicycle.

![](https://lh4.googleusercontent.com/BGk0qeFYcHBudtIbJdTHaCMtliOwqmI-u0H4gMq1WX7xeMULbM7B0b7a2ZZ1TXObx6yp1VCcxw0rm8150TVKaL_CNJ-Hua7r9EkEQNzxaVgEn_r4OBhJG0DSqq0CfB5KhZFG5eQQTZiv9Lp5UqOzFGSIIl2lxNMqfbgsGyOBibZy589peKrAGnFe2A)

The result from StarryAI is not so impressive in my opinion. However, it tried to capture the schoolboy and a bicycle. 

Next, I tried ‘a party on the moon’.

![](https://lh5.googleusercontent.com/p583W89E1_mt77uZcb-acH2h94bZQ5djaYmDr4go7DgF1reRpU0tDbmUCxyTAu4uvVnn3RoJF3K3HNTUV2AJxoaKg7Sc05A-esj0Vk5KyPUCv9SLup613bTnMreQu2LyKt1eNA2Dg3XSDXSkOGLapDE2hkORqtfIFkMYZDsbJsYtjFayu7kh7WWeNg)

Again, not as visually appealing. But I see different colors, perhaps indicating a party and moon-like circles.

### 4.  Rosebud
    

Rosebud product, Synth, is another platform that uses AI to convert text to impressive artwork. The platform can also create NFT-related artwork. It creates landscapes, objects, and characters in a matter of seconds.

Let’s put Rosebud’s Synth to the test. My first prompt was: a boy riding his bicycle.

![](https://lh3.googleusercontent.com/V6N2k2SfEt3cMXChYcCkSRfKUzL3lIagRBgsWD9goUCTeK1I4RN8Yu0ExlZ_8b0V2fc2H5MfLqPiLgWTQUYtC2EWO3cfUW5fq5ojSy66tjxU_wjOJTPN0NUF0mvnf6pCjY4U0u9cUR9Izf7UvYYpMthM-spmOaYoEl6Pig4_-ZySwUSR-X3YRXDnpg)

In my opinion, the image was not as top-notch as it should be. It appears that there is still some noise. However, it manages to capture a boy and a bicycle as objects.

My next prompt was: a party on the moon.

![](https://lh5.googleusercontent.com/S-djYbbmIudx27C92GR9OM1hy8dATQhVNCoSoIf1nowOuYrAQjqq6cRaJXrZ5ZuGeQvBTWHXolbq0ChimayB0BxGxQaGetmpEdLM12PqP39-vpkf0_ca0RtVFj-OPytXSTV7UQe_O3mw9qdY3fv7Se0nsP4TRV2C6T8N9py8__b94AaNeRMVeOM3Xg)

In my opinion, the quality of the image is not as crisp as Mid Journey. It struggles to capture the partying folks in spacesuits. It also struggles to visualize the moon. However, it made some progress in interpreting the text.

## Concerns on Generative Image Models

The text-to-image technology looks good on paper but there must be things to be put in check to avoid its misuse. First, many of the models frown from creating gory or violent images. Also, they avoid creating realistic images with the faces of popular figures. There are also copyright concerns with the images being used during training. This [<ins>study</ins>](https://arxiv.org/pdf/2105.09266.pdf) reveals some of the key copyright questions that have risen from the use of image generative models. For example, one can argue that the machine learning engineer does not own the copyright to use someone else’s artwork to train a machine learning model.

## Conclusion

Without a doubt, generative image models have unlocked new possibilities. The question now is: to what end? For one, such models will help humans visualize what they can imagine. Have you ever struggled to imagine how you’d look in an outfit? As an example, these researchers implemented an [<ins>image generation model</ins>](https://arxiv.org/abs/1908.08847) that creates realistic images of how humans would look in various outfits (a combination of tops and shorts). Asides from that, generative image models can be used to create more designs that are artistically pleasing, making artwork closer to humans like never before.