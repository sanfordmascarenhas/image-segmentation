# image-segmentation

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

A demo tensorflow code to learn and understand image segmentation with the MSCOCO dataset.

The dataset was mainly handled using pycocotools as the metadata was stored in annotations/filename.json

So make sure to run this in your environment.

```
pip install pycocotools
```

To learn more about how it works, visit [this repo](https://github.com/ppwwyyxx/cocoapi) from where it has been sourced from. I have tested the important functionality that we will use in this notebook as well for reference in the beginning.

For our demonstration, we will use just one category and the mask will be binary for making a simpler model and reducing processing time.

Our model will use transfer learning from pre-existing models. The encoder is MobileNetV2 and for the decoder we will use a conditional generative adversarial network called pix2pix to regenerate the image. This is necessary as the encoder will downsample the quality of the image to extract features and we will need the image again as it is part of our output. You will notice some skip connections to the decoder to upsample the image.

A camera has been added later to play with the model and it detects the person and the hand as well as part of the mask. It was origially supposed to work with video which is doable with some changes to the code. Just note that the fps will be limited as per the strength of your machine. Maybe a more portable version of the MobileNet or another encoder if we sacrifice some accuracy?


The final block to release the camera has been added in case the prior block fails and the camera is left on while the code is not running.


<br><br>
<hr>

### Main references used:
<br>
For pycoco library:<br>
https://towardsdatascience.com/getting-started-with-coco-dataset-82def99fa0b8<br>
https://github.com/ppwwyyxx/cocoapi

<br>
For model:<br>
https://www.tensorflow.org/tutorials/images/segmentation