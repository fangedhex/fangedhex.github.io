---
layout: post
title: 'Stable Diffusion: Part 2'
date: 2023-05-29 17:39 +0200
categories: [ai, stable-diffusion]
---

Welcome to a second part for Stable Diffusion where I give some advices I found or learnt to make better generated images.

## Default prompt

For the prompt, I always start with what I give below, it's a base that works very well for me.

### Positive

(For a realistic image)
```((realistic, photorealistic, raw photo)), ((masterpiece)), (8k, high quality, ultra high res), (highly detailed:1.2)```

(For a painting image)
```((realistic painting style)), ((masterpiece)), (8k, high quality, ultra high res), (highly detailed:1.2)```

### Negative
```low res, ((bad anatomy)), (low quality, worst quality:1.4), (monochrome:1.1), (lowres:1.1), disfigured, poorly drawn face, mutation, mutated, (low quality, worst quality:1.4, multiple limbs, creepy face, weird face, more than 2 hand, more than 2 arms, more than 2 legs, more than 2 feet, merged limbs, weird face, distorded body, distorded face), (missing finger, extra digits, fewer digits), ((mutated hands and fingers)), text, signature, deformed, ugly, poorly drawn hands, blur, blurry, (bad eyes:1.2), (misfigured pupils:1.2)```

## Models

I tested a lot of models to find the one I like the most for different image types.

### My most used models so far
* [AnythingV5](https://civitai.com/models/9409) for anime like images.
* [Dreamshaper](https://civitai.com/models/4384) for somewhat realistic images but still keeps a drawing like style.
* [ChilloutMix](https://civitai.com/models/6424) for realistic images.

### Models that I like and use sometimes
* [RevAnimated](https://civitai.com/models/7371)
* [Lyriel](https://civitai.com/models/22922)

## Negative embeddings ?!

I know about the negative embeddings, but I don't use them that often but I still try when I want to see if it can fixes an image I like.

## Making upscaled version of an image with more details

One thing I found out is that images upscaled using [4x-UltraSharp](https://mega.nz/folder/qZRBmaIY#nIG8KyWFcGNTuMX_XNbJ_g) are still bad if you zoom in a lot but the problem is that I can't make draw image more than 512x512 pixels without having an out of memory error.

For that, I installed [ControlNet](https://github.com/lllyasviel/ControlNet) with [its models](https://huggingface.co/lllyasviel/ControlNet-v1-1/tree/main) and a script named [Ultimate SD Upscale](https://github.com/Coyote-A/ultimate-upscale-for-automatic1111). I use control net to keep the img2img near the original with lowered denoising (0.15 seems like a good value but I check everytimes with X/Y/Z plot script to see the best value) and ultimate sd upscale will cut down the image into 512x512 chunks and upscale with the help of 4x-UltraSharp and add details to the final image.

## Sources

* [CivitAI : Model repository](https://civitai.com/)
* [Tutorial on how to use Ultimate SD Upscale](https://www.youtube.com/watch?v=yv4J4orS-SY)
