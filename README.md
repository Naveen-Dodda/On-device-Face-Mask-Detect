# On Device Face Mask Detect

It has been tough time with increasing spread of Covid-19, espcially for frontiline workers. I have seen staff at coffe shops, shipping centers, public spaces 
asking people to wear masks.I felt it would be safer and reduce risk for frontline workers, if we could automate face mask monitoring.
But it is important to respect everyone's privacy, so I decided to use a on device deeplearning solution. I am going to walk you through how I deployed a Face Mask
detection model on  [Coral Device](https://coral.ai/products/#prototyping-products).

## DataSet 

Right now you can find many open source datasets availabe, I have chosen a highly deversified [MAFA dataset](https://openaccess.thecvf.com/content_cvpr_2017/papers/Ge_Detecting_Masked_Faces_CVPR_2017_paper.pdf) which has images 35,806 manually annotated images.
You can try [Face Mask Detection](https://www.kaggle.com/andrewmvd/face-mask-detection?select=images) from kaggle as well.  

## Model 

As final goal of this project is to deploy it on coral device, I have choosen to start with [MobileNet SSD v2 (Faces)](http://download.tensorflow.org/models/object_detection/facessd_mobilenet_v2_quantized_320x320_open_image_v4.tar.gz) model.The anchor generator has been configured to
detect faces. You can find trained chekcpoints and models compiled for edge tpu above. 

## Demo

I am using coral [dev board](https://coral.ai/docs/dev-board/get-started/#requirements) to get started and [setup a camera](https://coral.ai/docs/dev-board/camera/#connect-a-usb-camera) 

git clone https://github.com/google-coral/examples-camera.git

cd examples-camera/gstreamer 
             (or)
cd examples-camera/opencv

python3 detect.py \
  --model Path_To_Be_Configured  \
  --labels Path_To_Be_Configured






## Transfer Learning

The most important aspect of this project is to choose right dataset that suits your environmet or work conditions. I have trained it on a generic dataset but if you
wish to optimize the model for your environment, transfer learning using the pretrained checkpoints is highly recommended. There are many ways to do this I have used 
object detection api, please find more details in [Google Colab here](https://colab.research.google.com/drive/1WA-FMMin7131-K_AeOXZxbmd62D4e-_I?usp=sharing). 


