#  I. Overview of algorithms 

   The VoxelGrid class and the ApproximateVoxelGrid class implement the voxel-based filtering method to downsample the point cloud. The octree also establishes voxels, so the octree-based voxels can also downsample the point cloud. In pclpy, the octree-based voxel downsampling is realized. There are two implementations: one is to use the octree to occupy the mean of the voxel point XYZ instead of all the points in the voxel, and the other is to use the octree to occupy the mean of the voxel XYZRGB instead of all the points in the voxel. The result of the final performance is that the point cloud obtained by using the calculation method of XYZ mean has no color information, and the point cloud calculated by using the XYZRGB mean has color, but the color change is the average of all points in the voxel RGB (detailed comments in the code). 

>  Note: This method is basically the same as ApproximateVoxelGrid, replacing the points in the voxels with the center points. The only difference is that ApproximateVoxelGrid can freely set the length, width and height of the voxels, while the octree can only be the voxels that build the cube. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574429025
  ```  
#  III. Display of results 

 ![avatar]( ceed01060f864f8da35c35aba7aef931.png) 

 (XYZ mean) voxel filtering (XYZRGB mean) voxel filtering  

