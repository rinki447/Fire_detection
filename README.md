# Forest Fire Detection

This project aims to detect forest fires using the FireNet and IEEE datasets. Follow the steps below to set up the project and run the detection.


Main file: Yolo.ipynb

Trained model: https://drive.google.com/file/d/1hgCh8dzRz1yjUsNQ6wNCZNxq01TY9vhs/view?usp=drive_link

## Setup and Training

1. Download the FireNet and IEEE data
2. Upload the FireNet data to Roboflow to obtain the data image API for faster data and annotation reading. Roboflow is basically an interface where we could upload our object detetcion datasets and get a corresposnding code key to read that data for training. 
3. With respeoct to pre-processing, we basically do horizontal fipping and rotation for the augmentation process
4. Copy the annotation API from Roboflow and paste it/ replace in the cell in "Yolo.ipynb". 
5. For instance, Open "Yolo.ipynb" and paste the data reading code that you got from RoboflowAPI and replace it in the 

```bash
!pip install roboflow

from roboflow import Roboflow
rf_ieee = Roboflow(api_key="ilXvK9f3xwRvE63aY9cK")
project_ieee = rf_ieee.workspace("new-workspace-ilks2").project("large_det")
dataset_ieee = project_ieee.version(1).download("yolov5")
```
Just replace it with the API key that you get from roboflow

6. Once the data is read is done, follow the instructions in the notebook to train. Basically the subsequent cells willguide you to the training process.

## Testing

6. To test, upload the videos/frames or images to a location in the drive or any other custom location. Also,  upload the best_ieee.pt model to any custom location. In the Yolo.ipynb, run the cell that contains the below code. Make sure the paths have been changed accordingly. Sample inference videos are avaialble at the sample_vids folder. 

```bash
!python detect.py --weights /content/drive/MyDrive/best_ieee.pt --img 640 --conf 0.4 --source /content/drive/MyDrive/field14.mp4 --save-txt
```
## Video

A detailed video explaining the same has been uploaded at demmo.webm

https://drive.google.com/file/d/1HXwqWGpAJjrvxGD0MmzPzoi6w3SRrcj6/view?usp=drive_link
# Fire_detection
