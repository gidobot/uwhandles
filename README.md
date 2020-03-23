# UWHandles
This is a meta repository for UWHandles dataset, which can be downloaded from this Google Drive link:  
[**[UWHandles]**](https://drive.google.com/file/d/1mZYeBiceVeo9dRYaCuJBaY63NufiA_fB/view?usp=sharing)

UWHandles is a dataset for 6D object pose estimation in underwater fisheye images. It provides 6D pose and 2D bounding box annotations for 3 different graspable handle objects used for ROV manipulation. The dataset consists of 28 image sequences collected in natural seafloor environments with a total of 20,427 annotated frames.

## File Structure
 ```
uwhandles
└───calibration  
│   │   fisheye_calib.yaml -> calibration file for fisheye  
│   │   rectified_calib.yaml -> calibration file for rectified fisheye  
└───data  
|   └───set#  
|       |   camera_poses.txt -> CSV file of globally referenced camera poses for each image in sequence, with each line formated as $image#, x, y, z, qw, qx, qy, qz$  
|       └───images  
|           |   annotations.json -> COCO style 6D pose and 2D bounding box annotations generated by the VisPose annotation tool for the image sequence  
|           │   annotations_culled.json -> culled annotations with bounding boxes regenerated for raw fisheye images  
|           └───raw -> folder containing raw fisheye images  
|           └───rect -> folder containing center rectified images    
└───image_sets -> contains text files which list the image sets for training, testing, and validation  
└───models  
    └───<object_name>  
    |   |   textured_real.obj -> obj files for the 3 different handle objects in the dataset with photo mapped textures  
    |   |   textured_real.glb -> glb files for the 3 different handle objects with additional material properties for more realistic rendering in Blender  
    └───rendered  
        └───<object_name> -> contains rendered images of the textured.obj models at different viewpoints
```
## Overview

Sample annotated sequence, showing center rectified images for visualization of the model handle projections

![Output sample](https://github.com/gidobot/gifs/raw/master/VisPose_Reviewer.gif)

The dataset was annotated using the VisPose annotation tool:  
[**[VisPose]**](https://github.com/gidobot/VisPose)

The sequence consistent camera poses for input to the VisPose annotation tool were generated using the ROS based [**TagSLAM**](https://berndpfrommer.github.io/tagslam_web/) package.

Below is a sample sequence showing the April tag detector and TagSLAM estimated camera poses

![Output sample](https://github.com/gidobot/gifs/raw/master/VisPose_AprilSLAM.gif)

## Citation
If you use this dataset, we request you to cite the following work.
```
@article{billings2020silhonet,
  title={SilhoNet-Fisheye: Adaptation of A ROI Based Object Pose Estimation Network to Monocular Fisheye Images},
  author={Billings, Gideon and Johnson-Roberson, Matthew},
  journal={arXiv preprint arXiv:2002.12415},
  year={2020}
}
```
