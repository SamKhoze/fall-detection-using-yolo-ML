# setup Project

## Create Env 
conda create --name falldetection python=3.8

## Activate conda env
conda activate falldetection

## Install all the dependencies
pip install -r requirements.txt


<h1> Human Falling Detection and Tracking </h1>

Using Tiny-YOLO oneclass to detect each person in the frame and use 
[AlphaPose](https://github.com/MVIG-SJTU/AlphaPose) to get skeleton-pose and then use
[ST-GCN](https://github.com/yysijie/st-gcn) model to predict action from every 30 frames 
of each person tracks.

Which now support 7 actions: Standing, Walking, Sitting, Lying Down, Stand up, Sit down, Fall Down.

## Data

This project has trained a new Tiny-YOLO oneclass model to detect only person objects and to reducing 
model size. Train with rotation augmented [COCO](http://cocodataset.org/#home) person keypoints dataset 
for more robust person detection in a variant of angle pose.

For actions recognition used data from [Le2i](http://le2i.cnrs.fr/Fall-detection-Dataset?lang=fr)
Fall detection Dataset (Coffee room, Home) extract skeleton-pose by AlphaPose and labeled each action 
frames by hand for training ST-GCN model.

## Pre-Trained Models

- Tiny-YOLO oneclass 
- SPPE FastPose (AlphaPose) 
- ST-GCN action recognition

## Usage
```
cd Yolo-model-implementation
python main.py -C 0
```


-------------------------------------------------------------------

# HumanFallDetection
We augment human pose estimation (openpifpaf library) by support for multi-camera and multi-person tracking and a long short-term memory (LSTM)
neural network to predict two classes: “Fall” or “No Fall”. From the poses, we extract five temporal and spatial
features which are processed by an LSTM classifier.

## Usage
```shell script
cd Human-Fall-Torch
python fall_detector.py
```
<TABLE>
<TR><TH style="width:120px">Argument</TH><TH style="width:300px">Description</TH><TH>Default</TH></TR>
<TR><TD>num_cams</TD> <TD>Number of Cameras/Videos to process</TD><TD>1</TD></TR>
<TR><TD>video</TD><TD>Path to the video file (None to capture live video from camera(s)) <br>For single video fall
                        detection(--num_cams=1), save your videos as abc.xyz
                        and set --video=abc.xyz<br> For 2 video fall
                        detection(--num_cams=2), save your videos as abc1.xyz
                        & abc2.xyz & set --video=abc.xyz</TD><TD>None</TD></TR>
<TR><TD>save_output</TD> <TD>Save the result in a video file. Output videos are
                        saved in the same directory as input videos with "out"
                        appended at the start of the title</TD><TD>False</TD></TR>
<TR><TD>disable_cuda</TD> <TD>To process frames on CPU by disabling CUDA support on GPU</TD><TD>False</TD></TR>
</TABLE>



