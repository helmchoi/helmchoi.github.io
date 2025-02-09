---
layout: post
title:  Running COLMAP in a command window (Windows 10)
categories: Notes
---

### Refer to:
https://colmap.github.io/faq.html

I wanted to fix camera intrinsics & extrinsics and run COLMAP.
To do that, first create three text files (camera.txt, images.txt, points3D.txt).

## Feature Extractor
If an error like '[option_manager.cc:811] Check failed: ExistsDir(*image_path)' pops up, try setting the image_path as a relative path, rather than the absolute path.
The command would look like this:
```
colmap feature_extractor --database_path PATH\database.db --image_path PATH\images --ImageReader.camera_model OPENCV --ImageReader.single_camera 1
```

## Feature Matching
```
colmap exhaustive_matcher --database_path PATH\database.db
```

## Point Triangulator
```
colmap point_triangulator --database_path PATH\database.db --image_path PATH\images --input_path PATH\sparse --output_path PATH\bin
```

## Saving the Model to txt
Saves the model and export to text files (camera.txt, images.txt, points3D.txt).
```
colmap model_converter --input_path PATH\bin --output_path PATH --output_type TXT
```

## Dense Reconstruction
### Image Undistortion
```
colmap image_undistorter --image_path PATH\images --input_path PATH\sparse --output_path PATH\dense
```
### Patch Match Stereo
```
colmap patch_match_stereo --workspace_path PATH
```
### Stereo Fusion
```
```
