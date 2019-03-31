# TD-OpenCV3TOP
## Touchdesigner OpenCV3 C++ TOP for FaceDetect

_**Contributors**_

- **Da Xu** - *Development and Documentation*
- **[Greg Finger of PLGRM Visuals](https://github.com/gregfinger)** - *Demo Projects, Testing and Foreman*



This plugin adds the OpenCV FaceDetect functionality to TD via a C++ TOP. 


Though OpenCV is already integrated into TD, it's done via Python, which is not terribly convenient when you have to deal with streams of data. This plugin now allows you to pipe data from any TOP straight into the OpenCV algorithms and spit out data in way that can be acted upon immediately. It makes the whole process much more streamlined and faster.


## Release Notes v1.5 3/31/2019
Yes, we skipped over a few minor versions. But since we added quite a few things to this release, we feel we deserve the 1.5.


- The plugin is now **cross-platform**. We now have binary releases for both **Mac** and **Windows**, along with the necessary code and project files to build it on your own, if you so choose.
- The plugin now supports Touchdesigner **Stable** and **Experimental** builds. The Experimental builds implemented a new way of dealing with C++ plugins, and they allow users to use C++ plugins without a Commercial or Pro License. Make sure you use the correct binary for the build of TD you are using.
- Greg Finger has provided a demo toe file for the Experimental builds.
- Extensive updates have been made to the documentation. We now includes instructions on how to build OpenCV on Mac, as well as build instructions for the plugin.




## FEATURES

- Once face(s) has been detected, the detected face(s)' info are passed out via **Info Dat AND Pixel Packing**.
Info is packed into the output frame (RGBA32Float) in the following manner:

- The 1st Pixel's R contains how many faces have been detected. 

- I use the RGBA channels of the subsequent pixels to keep (x, y, width, height) of the detected face, in the order that they have been detected.


- There is a Sanity Check toggle that let's you see exactly what the detector sees.


Please check Greg Finger's demo Touchdesigner project to see how to use this C++ TOP. AGAIN, you WILL NEED a Commercial or Pro license.

## Additional Notes
I have exposed most of the parameters of the detectMulti call as custom parameters. Min and Max search sizes have been expressed as a ratio in relation to the input height. You can drop an Info TOP down to see the exact size of each in pixels.



Try different cascade files, they do effect result and speed. You can find additional cascade files in the OpenCV3 distro.



## Demo
I have included a compiled version of the DLL. However, you still need to download the OpenCV dlls from opencv.org to make the demo run. You also need the latest version of Touchdesigner, which at this moment is 2018.25000. 

You need to put the opencv world dll into the same directory as OpenCV3TOP.dll. 

Specific instructions below:

1. Goto opencv.org, under Releases, download the Win Pack. 

2. Run the resulting exe file. It will ask you to extract the lib to somewhere. Find a nice place for it, and extract

3. Once the extraction is done, open up Explorer, and go to the dir that you have extracted to. 

4. There should be an opencv dir, go into it, and then goto build\x64\vc14\bin. 

5. Copy the opencv_world341.dll to the Demo/TD-cppFace-reduced/Data/ dir, essentially where my dll lives and is referenced, that you got from my github. NOTE: DO NOT COPY THE opencv_world341d.dll. That's for debugging. It's hella slow.

opencv\build\etc contains the cascade files you need. The names are self-explanatory.
