# 3D-GT-tools
List of tools for creating ground truth annotations for 3D data

## Napari

Napari without any additional plugins is a simple and relatively nice option suitable both for correcting existing labels and creating new annotations

### Scope
Semantic or instance segmentation from scratch or correcting existing labels

### How to annotate
- Load image as `image` layer and either load exiting segmentation or create a new `labels` layer
- Use `labels` layer's instruments to correct labels

![Napari_annotate_one_cell](https://github.com/kreshuklab/3D-GT-tools/assets/89460016/28fbcb01-7163-4917-b989-7ce51522c5a0)


### Tips
- keys `1` to `5`: switch between tools: eraser, paint brush, bucket, color picker and move
- `v`: toggle visibility of the current layer
- `m`: set to new label (like if you want to annotate a new object that was completely missing before)
- - `[` and `]` to change brush size
- Other key combinations in `File -> Preferences -> Shortcuts`
- `n edit dim`: if set to `2` - corrections affect only current layer, if set to `3` - extend to the volume.   
  Setting to `3` for paint brush results in drawing with a ball of a given size in 3D space, which makes labeling in 3D more smooth and quick, but it's easy to paint something wrong if the object changes quickly between frames.  
  For bucket setting to `3` means joining masks, which can be useful for correcting instance segmentation.
- `Ctrl+Z` works
- I found it useful to play with the contrast of the image layer to see the borders of noisy objects more clearly
- Change visible axes with `Ctrl + E` to check that the annotations are consistent in 3D


### Limitations
- No "smart" annotation, it's really just for painting things by hand
- The size of the data is limited by what Napari can deal with, so the data has to fit in the memory
- If the volume is on a bigger side (`~500x500x500` pixels and more) and there are many instances, bucket tool will be very slow and might even cause Napari to crash if applied in 3D



## Cellpose 2.0 GUI


### Scope
Instance segmentation. The labeling work by drawing freehand closed lines in 2D using GUI.
Label mask can be saved as `png`, `tif` or `numpy`

### How to annotate
A complete [guide](https://cellpose.readthedocs.io/en/latest/gui.html#using-the-gui) for using `cellpose` gui is recommended. A small demo video of labeling 1 cell in 3D image is provided [here](https://oc.embl.de/index.php/s/Yb9JT2X5FcAxXFr)

### Tips
- One can try to run pretrained model to predict a label mask and then delete erroneous labels and redraw then using drawing tools
- Use short keys as described in the guide for faster/easier handling of different GUI functionalities
  - Uncheck `single stroke` option to draw in 3D


### Limitations
- Time-consuming as one has to label an object in each slice
- No automated object neighborhood detection or holes filling: you get what you draw as a label masks
- Very slow for large image data files
