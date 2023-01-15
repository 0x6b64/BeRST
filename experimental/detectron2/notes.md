# Experiment: Instance && semantic segmentation using detectron2

Objective: 

To be able to track the full object associated with the fiducial marker.

Plan:

0. (completed) Setup docker container with Detectron2

References:
* https://github.com/facebookresearch/detectron2
* https://detectron2.readthedocs.io/en/latest/tutorials/getting_started.html#inference-demo-with-pre-trained-models


```bash
# Reusing the publically available ec2 DLC.
# https://github.com/aws/deep-learning-containers/blob/master/available_images.md
docker run --privileged --security-opt seccomp=unconfined --gpus all -d -it --name detectron-dev --mount type=bind,source=/home/ec2-user/BeRST/,target=/BeRST  763104351884.dkr.ecr.us-east-1.amazonaws.com/pytorch-training:1.13.1-gpu-py39-cu117-ubuntu20.04-ec2
docker exec -it 6f639e0ba640aaeeb0cc487e92953d9147933de25e30b82f18c7633344242f80 bash 
pip3 install opencv-python

git clone https://github.com/facebookresearch/detectron2.git
python -m pip install -e detectron2
```

0. (completed) Create demo script to understand how to use the detectron2 API.

Next, to create a standalone python application to do the following.

0. Use the webcam input or video input which feeds directly into any of the pretained COCO-ImageSegmentation models to preform inference. Use this script as reference: https://github.com/facebookresearch/detectron2/blob/main/demo/demo.py

0. Get the inference result object and isolate the generated image masks. 

0. Get the location of the fiducial marker && chose the mask which overlaps meaningfully with it. This may have edge cases, but we can choose the segment with the greatest overlap.

0. Overlay the selected mask on the annotated output - webcam/video. 

0. Merge into primary detection pipeline. 