#  Introduction to the principle 

##  1. Create a KD tree 

 ![avatar]( 20210516160551664.png) 

   A kd-tree data structure is a data structure used in computer science to organize data with several points in k-dimensional space. It is a binary search tree with other constraints. K-d trees are very useful for range searches and nearest neighbor searches. For our purposes, we usually only deal with 3-D point clouds, so all our k-d trees are 3-D. Each layer of the K-d tree uses a hyperplane perpendicular to the corresponding axis, dividing all the children along a specific dimension. At the root of the tree, all the sub-nodes will be split according to the first dimension (i.e. if the first-dimensional coordinate is less than the root, it will be in the left subtree, if it is larger than the root, then it will be obviously in the right subtree). Each layer in the tree is divided on the next dimension, returning to the first dimension once all the other dimensions have been exhausted. The most efficient way to build a k-d tree is to use a partitioning method: place the middle point at the root and everything has a smaller one-dimensional value, smaller on the left and larger on the right. Then, repeat this process on the left and right subtrees until the last tree to be partitioned consists of only one element. Figure 1 is a schematic diagram of a two-dimensional data search with k = 2. Each layer of the kd-tree is a dimension of the data, and a sub-node is used to split the dimensional data interval. The data smaller than the node value in this dimension is placed in the left subnumber, and the data larger than the node value is placed in the right subtree. Each layer of the kd-tree is separated in the next dimension of the data. When the dimensions of the data are used up, it returns to the first dimension and continues to iterate until the searched data is determined. This method reduces the time complexity to. Creating a kd-tree usually uses the median value of each dimension of the data value as the segmentation hyperplane.  

   In the process of 3D point cloud data search, KD-tree also realizes the fast retrieval of 3D point cloud data by one-dimensional hyperplane perpendicular to the point cloud and recursively dividing the space into multiple subspaces. 

##  2. Neighborhood search 

 ![avatar]( 20210516163024278.gif) 

   The image below is a demonstration of how the nearest neighbor search works.  

#  Algorithm flow 

##  1. Read the point cloud and build a KDTree 

   This is the preprocessing step for the nearest neighbor query. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574433692
  ```  
##  2. Select the query point 

 The code below uses the 200th point as the query point. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574433692
  ```  
##  3. K-nearest neighbor search 

   search_knn_vector_3d returns an index list of the k nearest neighbors of the query point. These adjacent points are stored in the array numpy, and all points in the numpy array are colored (rendered green [0, 1, 0]) using pcd.colors. The first index point is skipped here because it is the query point itself. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574433692
  ```  
##  4. Radius neighborhood search 

   Use search_radius_vector_3d to query all points that are less than a given radius 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574433692
  ```  
##  5. Mixed search 

   In addition to KNN search (search_knn_vector_3d) and RNN search (search_radius_vector_3d), Open3d also provides a hybrid search function (search_hybrid_vector_3d). It returns up to K closest neighbors that are less than a given radius from the query point. This function combines KNN and RNN search conditions and is also referred to as RKNN search in some literature. It has performance advantages in many cases and is widely used in Open3d's functions. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574433692
  ```  
#  III. Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574433692
  ```  
#  IV. Display of results 

 ![avatar]( 20200826165149929.png) 

#  V. Remarks 

 ![avatar]( 20210404090231393.jpg) 

   When using k-nearest neighbor search in the same point cloud, the "k" nearest neighbor points here include the queried point itself. For example, to search for 5 points closest to the black point, when "k = 5" in the parameter, the nearest neighbor points are shown in red. In fact, in the case of not including its own point, the searched points are "k-1" points in the neighborhood of that point.  

