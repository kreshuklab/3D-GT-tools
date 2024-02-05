# 3D-GT-tools
List of tools for creating ground truth annotations for 3D data

## Napari

Napari without any additional plugins is a simple and relatively nice option suitable both for correcting existing labels and creating new annotations

### Scope
Semantic or instance segmentation from scratch or correcting existing labels

### How to annotate 
- Load image as `image` layer and either load exiting segmentation or create a new `labels` layer
- Use `labels` layer's instruments to correct labels

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
- I found it useful to play with the contrast of the image layer to see the borderes of noisy objects more clearly
- Change visible axes with `Ctrl + E` to check that the annotations are consistent in 3D


### Limitations
- No "smart" annotation, it's really just for painting things by hand
- The size of the data is limited by what Napari can deal with, so the data has to fit in the memory
- If the volume is on a bigger side (`~500x500x500` pixels and more) and there are many instances, bucket tool will be very slow and might even cause Napari to crash if applied in 3D



## Name

### Scope

### How to annotate 

### Tips

### Limitations