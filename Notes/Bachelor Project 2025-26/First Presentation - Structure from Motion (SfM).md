### Source One
[‘Structure-from-Motion’ photogrammetry: A low-cost, effective tool for geoscience applications](file:///home/benedikt-felsch/Documents/Bachelor%20Project/First%20Presentation/1-s2.0-S0169555X12004217-main.pdf)

### Source Two
[Assessment of Forest Structure Using Two UAV Techniques: A Comparison of Airborne Laser Scanning and Structure from Motion (SfM) Point Clouds](file:///home/benedikt-felsch/Documents/Bachelor%20Project/First%20Presentation/forests-07-00062.pdf)


#### Question One: Wie funktioniert die photogrammetrische Rekonstruktion von 3D-Punktwolken aus 2D-Bilddaten?

![[SfM-Workflow.png]]

- SIFT = Scale Invariant Feature Transform 
	- used to identify features in each image that can be automatically recognized in other images even in different scales rotations and locations
- Bundler is used to extract a sparse point cloud
	- tracks (compromising a minimum of two keypoints and three images) used for point-cloud reconstruction
		- using this method transient features and non-static objects are automatically removed
	- reconstructs camera position and orientation
	- resulting point cloud is in a relative coordinate system
- CVMS = Clustering View for Multi-View Stereo
	- uses the reconstructed camera positions from Bundler to decompose overlapping input images into clusters of manageable size
- PVMS2 = Path-based Multi-View Stereo
	- reconstructs 3D data from the CVMS clusters
	- results in a significant increase in point density, roughly two orders of magnitude
- GCP = Ground Control Points
	- are used to transform the model from relative coordinates to world coordinates
		- have to be identified manually
- significant outliers and artefacts as well as unnecessarily reconstructed topography are removed manually
- the raw point cloud is decimated to a regular grid in order to reduce high point density as well as remove the effects of 'off-ground' features
	- provides a first-order bare-earth elevation model
	- this may be unwanted depending on final application
#### Question Two: Welche Vor- und Nachteile bietet die photogrammetrische Rekonstruktion von 3D-Punktwolken im Vergleich zur Erfassung mit LiDAR-Sensoren?
- no need for specialized Hardware, consumer grade cameras are sufficient to procure data/images
- generally cheaper
- data acquisition similarly fast or even faster
- post processing time significantly longer
- similar density of point clouds
- 94% of overlapping model differences in the range \[-1m, 1m\] and 86% between \[-0.5m, 0.5m\]
- dense vegetation cover may prove problematic for effective terrain reconstruction
	- also including grass, snow and sand
- lack of precision for dense canopy cover 