Code for "Unsupervised Discovery of Object Landmarks as Structural Representations"
=====

Project page: http://www.ytzhang.net/projects/lmdis-rep/

## Paper

Yuting Zhang, Yijie Guo, Yixin Jin, Yijun Luo, Zhiyuan He, Honglak Lee,
"**Unsupervised Discovery of Object Landmarks as Structural Representations**,"
*IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, June 2018. [[arxiv](https://arxiv.org/abs/1804.04412)]

## What are included
For experiment on CelebA and AFLW dataset
- Demo using pretrained models (detection and visualization on individual images)
- Training code
- Evaluation code

## Data to download

- The [CelebA](https://drive.google.com/drive/folders/0B7EVK8r0v71pWEZsZE9oNnFzTm8) dataset, saved in the `data/celeba_images` folder.
- [ground truth landmark annotation](http://files.ytzhang.net/lmdis-rep/release-v1/celeba/celeba_data.tar.gz) for pre-processed CelebA images, saved in the `data/celeba_data`.
- The [AFLW](http://files.ytzhang.net/lmdis-rep/release-v1/aflw/aflw_images.tar.gz) dataset of preprocessed images, so that the face is on the similar position as face in CelebA images, saved in `data/aflw_images` folder.
- [ground truth landmark annotation](http://files.ytzhang.net/lmdis-rep/release-v1/aflw/aflw_data.tar.gz) for pre-processed AFLW images, saved in `data/aflw_data` folder.

## Pretrained Models to download

The pretrained models for CelebA dataset can be obtained via [this link](http://files.ytzhang.net/lmdis-rep/release-v1/celeba/celeba_pretrained_results.tar.gz), which detect 10 or 30 landmarks on the image. 

The pretrained models for AFLW dataset can be obtained via [this link](http://files.ytzhang.net/lmdis-rep/release-v1/aflw/aflw_pretrained_results.tar.gz), which detect 10 or 30 landmarks on the image.

Running `./download_celeba.sh` and `./download_aflw.sh` will automatically download pretrained models and data for experiment on each dataset. The pretrained model will be saved in `pretrained_results/celeba_10`, `pretrained_results/celeba_30`, `pretrained_results/aflw_10`, `pretrained_results/aflw_30`. And the data will be saved in `data/celeba_data`, `data/aflw_data`, `data/aflw_images`. Note that you should download the CelebA data by yourself into `data/celeba_images` 

## Demo on CelebA image samples using pre-trained model (quick demo)

You can run a quick demo on CelebA images.

- Download our pretrained model on CelebA.
- Put the pretrained model in the same directory as defined in `one_step_test_celeba_demo.sh`, the directory is `pretrained_results/celeba_10` or `pretrained_results/celeba_30`
- After that, run
	
		./one_step_test_celeba_demo.sh
	
- You should be able to view the visualization of the landmark discovery results in the `demo/output` folder created under the root of the project. If `SPECIFIC_MODEL_DIR` is `pretrained_results/celeba_10`, there are 10 detected landmarked on each image. If `SPECIFIC_MODEL_DIR` is `pretrained_results/celeba_30`, there are 30 detected landmarked on each image. 

To perform detection on other human face images, you can just put the images you are interested in into the `demo/input` folder, and rerun `./one_step_test_celeba_demo.sh` to see the detected landmarks on these images in `demo/output` folder.

## Training 

- Train the model on CelebA dataset for 10 landmarks: `python exp-ae-celeba-mafl-10.py`
- Train the model on CelebA dataset for 30 landmarks: `python exp-ae-celeba-mafl-30.py`
- Train the model on AFLW dataset for 10 landmarks: `python exp-ae-aflw-10.py`, the AFLW is finetuned based on pretrained model for CelebA dataset, so we must have `pretrained_results/celeba_10` downloaded.
- Train the model on AFLW dataset for 30 landmarks: `python exp-ae-aflw-30.py`, the AFLW is finetuned based on pretrained model for CelebA dataset, so we must have `pretrained_results/celeba_30` downloaded.

## Evaluation

- Test the model on CelebA dataset `./one_step_test_celeba.sh`
- Test the model on AFLW dataset `./one_step_test_aflw.sh`

In `one_step_test_celeba.sh` or `one_step_test_aflw.sh`, you can specify `SPECIFIC_MODEL_DIR` as the path of folder saving the trained checkpoint, and `SNAPSHOT_ITER` as the number of snapshot step you would like to test. If the snaphot step is not specified, the script automatically test on the lastest checkpoint.

## Remarks

Models on other datasets and more code updates are coming soon. 
