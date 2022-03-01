![](/img/scanAR.png)

# scanAR
This is the repository for a GitHub pages based website to experiment with based AR visualization prototypes.
[https://scanar.github.io/](https://scanar.github.io/)

# Get started with AR
1. Print this marker on paper such that it is about 6cm wide.
<img src="/img/206_border.png" alt="https://github.com/scanAR/scanar.github.io/blob/master/img/206_border.png" width="200">

2. Head over to: [https://scanar.github.io/](https://scanar.github.io/), allow the webcam to start, hold up the marker, and enjoy the AR magic!

<img src="/img/test_bunny.gif" alt="https://github.com/scanAR/scanar.github.io/blob/master/img/test_bunny.gif" width="200">

# Contributing
If you want to help feel free to fork this repository and propose changes in a pull request. Also feel free to approach the developers to request to _join the team_ of developers.

# How to render a 3D model using AR
The code below is a snippet of how one can render an OBJ model based on a marker.

```html
<!DOCTYPE html>
<html>

<script src="https://aframe.io/releases/1.0.4/aframe.min.js"></script>
<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>

<body style="margin : 0px; overflow: hidden;">    
      <a-scene embedded arjs='sourceType: webcam; debugUIEnabled: false; detectionMode: mono_and_matrix; matrixCodeType: 4x4_BCH_13_9_3;'>

          <a-marker type='barcode' value='206'>
              <a-entity obj-model="obj: url(bunny.obj); mtl: url(bunny.mtl)"></a-entity>
          </a-marker>

      <a-entity camera></a-entity>
    </a-scene>
</body>

</html>

```

Specifically the following code helps render a 3D model called `bunny.obj` whose shading is defined with the aid of `bunny.mtl` (which in turn requires `bunny.png`). The 3D model is rendered using the `barcode` marker number `206`.

```html
<a-marker type='barcode' value='206'>
    <a-entity obj-model="obj: url(bunny.obj); mtl: url(bunny.mtl)"></a-entity>
</a-marker>
```

Therefore to render an alternative model users may replace the model, and optionally also the marker used.

# Markers
Markers can be found in the `/markers` folder. Currently the code uses markers of the type `4x4_bch_13_9_3` which are contained in the folder [`/markers/4x4_bch_13_9_3`](https://github.com/scanAR/scanar.github.io/blob/master/markers/4x4_bch_13_9_3). To test a marker, print it such that the black square is about 4cm in size, and ensure it has a white border of about 1 cm. An example for [marker `206`](https://github.com/scanAR/scanar.github.io/blob/master/markers/4x4_bch_13_9_3/206.png) is shown below. 

<img src="/img/206_border.png" alt="https://github.com/scanAR/scanar.github.io/blob/master/img/206_border.png" width="200">

**Source:** [https://github.com/nicolocarpignoli/artoolkit-barcode-markers-collection](https://github.com/nicolocarpignoli/artoolkit-barcode-markers-collection)


# Background and resources

* AR-js documentation: https://ar-js-org.github.io/AR.js-Docs/

* AR-js repository https://github.com/AR-js-org/AR.js

* Repository for emscripten port of ARToolKit to JavaScript: https://github.com/artoolkitx/jsartoolkit5

* Old ARToolKit site https://www.wikiwand.com/en/ARToolKit

* ARToolKit was originally presented in:
H. Kato and M. Billinghurst, *“Marker tracking and HMD calibration for a video-based augmented reality conferencing system”,* in Proceedings 2nd IEEE and ACM International Workshop on Augmented Reality (IWAR’99), Oct. 1999, pp. 85–94. doi: [https://doi.org/10.1109/IWAR.1999.803809](https://doi.org/10.1109/IWAR.1999.803809).     
See also [this open access link](http://www.hitl.washington.edu/artoolkit/Papers/IWAR99.kato.pdf)
