# MMD2depth
**[Download](https://github.com/KurisuMakise004/MMD2depth/raw/main/MMD2UDP_win.7z)** |
**[Google Colab](https://colab.research.google.com/github/KurisuMakise004/MMD2depth/blob/main/COLAB.ipynb)**

[MMD2depth](https://github.com/KurisuMakise004/MMD2depth) is a tool for converting [MikuMikuDance](https://sites.google.com/view/vpvp) models (.pmx) with motions(.vmd) to depth images sequences for use with depth2img scripts in [Stable Diffusion 2.0](https://github.com/KurisuMakise004/stablediffusion).

This tool is based on the [MMD2UDP](https://github.com/KurisuMakise004/MMD2UDP), which converts MMD to [UltraDensePose](https://github.com/transpchan/transpchan.github.io/blob/57efe17cdce35cf2c49c8d11ebd9bac108d1ac59/live3d/CoNR.pdf). 


## Usage

Using this tool for commercial purposes is allowed. However, you will still need to ask for permission if you are using the MMD models created by someone else.

1. Create a ZIP file named `model.zip` with all your MMD files (your_model.pmx, and textures). Note that tar, 7z, rar, or other formats are not supported.
2. Rename your motion file to `motion.vmd`, and optionally your camera file to `camera.vmd`.
3. Put `motion.vmd`, `camera.vmd` and `model.zip` into the same folder as `UltraDensePose.exe`.
4. Run UltraDensePose.exe and wait for the results in the `output` folder. The process might take very long for models with complicated physics setups, as the conversion process need to go through your `motion.vmd` and compute for each frame to obtain an depth image sequence.
5. Read it with 
```
cv2.imread("./output/0001",  cv2.IMREAD_ANYCOLOR | cv2.IMREAD_ANYDEPTH | cv2.IMREAD_UNCHANGED)
```

## Configuration files

You can configure `orthographic`, `framerate`, `frameoffset`, `udpaxis` (allowed values: UDPXYZ/UDPZXY/UDPXZY/DEPTH) by creating a file with the respective name.
