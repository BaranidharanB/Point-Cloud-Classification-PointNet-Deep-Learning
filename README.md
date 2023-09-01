# Point-Cloud-Classification-PointNet-Deep-Learning

- Point cloud is an important type of geometric data structure. Due to its irregular format, most researchers transform such data to regular 3D voxel grids or collections of images. This, however, renders data unnecessarily voluminous and causes issues. In this paper, we design a novel type of neural network that directly consumes point clouds and well respects the permutation invariance of points in the input. Our network, named PointNet, provides a unified architecture for applications ranging from object classification, part segmentation, to scene semantic parsing. Though simple, PointNet is highly efficient and effective. Empirically, it shows strong performance on par or even better than state of the art. Theoretically, we provide analysis towards understanding of what the network has learnt and why the network is robust with respect to input perturbation and corruption.


# PointNet Architecture

![Screenshot 2023-09-01 at 1 09 43 AM](https://github.com/BaranidharanB/Point-Cloud-Classification-PointNet-Deep-Learning/assets/118863352/6999159e-fcd3-426c-b869-59a63dff8209)

- The architecture is surprisingly simple and quite intuitive. The classification network uses a shared multi-layer perceptron (MLP) to map each of the n points from three dimensions (x, y, z) to 64 dimensions. It’s important to note that a single multi-layer perceptron is shared for each of the n points (i.e., mapping is identical and independent on the n points). This procedure is repeated to map the n points from 64 dimensions to 1024 dimensions. With the points in a higher-dimensional embedding space, max pooling is used to create a global feature vector in ℝ¹⁰²⁴. Finally, a three-layer fully-connected network is used to map the global feature vector to k output classification scores. The details on the “input transform” and “feature transform” are covered in the “Transformation Invariance” section below.

- As for the segmentation network, each of the n input points needs to be assigned to one of m segmentation classes. Because segmentation relies on local and global features, the points in the 64-dimensional embedding space (local point features) are concatenated with the global feature vector (global point features), resulting in a per-point vector in ℝ¹⁰⁸⁸. Similar to the multi-layer perceptrons used in the classification network, MLPs are used (identically and independently) on the n points to lower the dimensionality from 1088 to 128 and again to m, resulting in an array of n x m.

# 3DShapeNets Dataset Table Image

![Screenshot 2023-09-01 at 1 14 46 AM](https://github.com/BaranidharanB/Point-Cloud-Classification-PointNet-Deep-Learning/assets/118863352/6b384c39-8c3d-4315-b4cd-d53e4db596be)

# Generated pointcloud of the object

![Screenshot 2023-09-01 at 1 16 41 AM](https://github.com/BaranidharanB/Point-Cloud-Classification-PointNet-Deep-Learning/assets/118863352/8c3f5a33-5455-4d64-ba8b-3b302e7134c6)

# Training the Model with 10 epochs 

![Screenshot 2023-09-01 at 1 17 51 AM](https://github.com/BaranidharanB/Point-Cloud-Classification-PointNet-Deep-Learning/assets/118863352/37dd6699-fd2c-4cad-9064-e911e5409507)

# Classifying with random data from the dataset with predicted classes and labels

![image](https://github.com/BaranidharanB/Point-Cloud-Classification-PointNet-Deep-Learning/assets/118863352/600c3550-b6af-4f45-aae5-7fd9fe010fdf)


# Reference: 
- https://arxiv.org/abs/1612.00593
- https://github.com/aldipiroli/pointnet/tree/main
- https://medium.com/@sanketgujar95/https-medium-com-sanketgujar95-pointnet-5e07b01515e2
- https://medium.com/mlearning-ai/point-net-for-classification-968ca64c57a9
  
