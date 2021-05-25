# MASK-DECTECTION-YOLO-V$
Mask Detection using YOLO v4. 

# Steps to execute:
-  Create Dataset
    * Collect all images. Classes should be balanced.
    * Augement dataset using tools like RoboFlow, etc.
    * Anotate images to convert into txt file(Yolo input data format) using tools like LabelImg,Bbox etc.
    * Create train.txt which contains path of all input data will be used in training.
    * Create test.txt which contains path of all input images will be used in validation.

- Download Darknet
  * <a href = "https://github.com/AlexeyAB/darknet.git">Darknet GIT Repo.</a>

- Compile 
  * Use ./make command from command line to compile all C++ files.

- Download Predefined weights
  * <a href="https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.conv.137">yolov4.conv.137</a>

- Prepare Input data format structure
  * Copy Input data from step 1 to data folder under darknet folder
  * Create .names files which contains classes which need to detect.
  * Create .data files contains
    - classes= no of classes
    - train  = data/train.txt  
    - valid  = data/test.txt  
    - names  = data/mask.names  
    - backup = backup/ [where all weight files be stored]

- Train model 
  * !./darknet detector train .datafile_path configfile_path weightfile_path -dont_show -i 0 -map 

- Test Model
  * Test against images<br>
   !./darknet detector test data/mask.data cfg/yolov4-custom.cfg backup/yolov4-custom_last.weights TESTDATA/JEN.jpeg  -thresh 0.3
 imShow('predictions.jpg')
  * Test against video<br>
    !./darknet detector demo data/mask.data cfg/yolov4-custom.cfg backup/yolov4-custom_best.weights -dont_show TESTDATA/MASK_TEST.mp4 -i 0 -out_filename TESTDATA/prediction.avi
    
    
 - Model Evaluation: 
 
| Parameter | Count |
| :---: | :---: |
| TRAIN DATA | 5000 |
| MASK | ap = 92.73%  |
| NOT MASK | ap = 82.81% |
| precision | 0.87 |
| recall | 0.89 |
| F1-score | 0.89 |
| mean average precision (mAP@0.50) | 0.877713, or 87.77 % |
| FPS | AVG:52 |
| Total Detection Time | 5 Seconds |

# Weight Files:
<a href = "https://drive.google.com/drive/folders/15auDz5V4IdwyGdlZ8N5GWeqvPPOJ7xcQ?usp=sharing">Trained Weights</a>



# Predictions:
<img src="https://github.com/maha-prathamesh/MASK-DECTECTION-YOLO-V4-/blob/main/Pred.gif" height="500" width="800"/>
<br>
<img src="https://github.com/maha-prathamesh/MASK-DECTECTION-YOLO-V4-/blob/main/TEST_DATA_PRED_2.jpg" height="300" width="600"/>
</br></br>
<img src="https://github.com/maha-prathamesh/MASK-DECTECTION-YOLO-V4-/blob/main/predictions.jpg" height="300" width="600"/>
