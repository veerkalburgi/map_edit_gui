# map_edit_gui
pcd map editor pkg


This is a point cloud editor can be used to delete/patch/save point cloud for pcd map.
> With help of Rviz visualizer  is used to edit the point cloud map

> This tool can patch the holes on the ground using RANSAC to find the optimal plane!
This application comprises two parts:
1. Customized rviz tools for the editing functions.
2. The ros node that read pcd files and provides editing functions with algorithms (for example, segmentation for wall removal.).

* The region growing algorithm is used to segment the whole point cloud when .pcd is imported.
  
  * The first tool in Rviz is used to edit the point cloud by selecting clusters.
  
  * The second tool in Rviz is used to edit the point cloud by selecting points


## Required package
[pcl_ros](http://wiki.ros.org/pcl_ros)

## How to play?
```
roslaunch ground_pointcloud_editor test.launch
```


## Documentations
Two tools with functions are implemented for Rviz. Users just need to use these two tools to edit the point cloud in Rviz.


### Button of selected clusters
The selections will be on the clusters, all operations will be affected on clusters.
The topic GED_current_selected_clusters shows the selected point cloud.
```
Keyboard d:

Delete selected clusters:
```

The selection from z axis is sliced selection, it only selects clusters from max_z to max_z-1.0 which is useful for multiple floors editing.


```
Keyboard w:

Delete wall clusters: 
```


```
Keyboard r:

Reset all clusters: 
```

```
Keyboard k:

Save result point cloud in /tmp/ground.pcd with pcl::PointXYZ format
```

```
Keyboard z:

Return to last step
```


### Button of selected points
The selection is implemented with aggregated selection.
The topic GED_current_selected_points shows the selected points.

```
Keyboard p:

Patch ground points around selected points:
```
RANSAC is used to find the plane of selected points and fill the hole by iterating the selected area.



```
Keyboard c:

Clear aggregated points selection:
```


```
Keyboard d:

Delete selected points:
```



