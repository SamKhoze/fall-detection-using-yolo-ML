Create Env 
conda create -p env/ python=3.8

Install all the dependencies
pip install -r requirements.txt


To test yolo model implementation
- cd Yolo-model-implementation
- python main.py -C 0  #(-C for camera)


To test torch model implementation
- cd Human-Fall-Torch
- python fall_detector.py
