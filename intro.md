# Sampling data with transforms

[napari] is a viewer for n-dimensional data. Internally it is built of objects
like `Layer`, `Dims` and `Viewer` that have certain responsibilities as part
of the application's rendering pipeline.

Development has focused on solving certain issues that are a bit endemic to
working with n-dimensional data and creating a viewer:

* How are the dimensions of the data mapped to the viewable dimensions of the
  viewer?
* For large datasets, how do we subset the data to fit in the viewer?
* How do we handle asynchronous data loading?
* How do we handle transforms?

Here we'll try to build a toy viewer from scratch. The goal is to identify the
key decisions that get made along the way and to explain them in detail. At
the end, we hope to have a common language for describing the design and will be
able to see which `napari` objects are involved with the key rendering
responsibilities. 

[napari]: https://napari.org