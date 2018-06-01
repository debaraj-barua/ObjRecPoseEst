- $`conda install matplotlib numpy sympy scipy pytest\`
- PIL pydot progressbar ipython ipykernel
---
- $`script log-terminal.txt`
- $`env MKL_THREADING_LAYER=GNU python main_train_dagnet.py ../configs/linemod_ras_o3_rgbd_dagnet.ini`
- $`exit`


---
# common error:

## meadian blur 
`
 File "/home/dbarua2s/ObjRecPoseEst/src/util/misc.py", line 101, in addNoiseToTrainSeqs
    fractNoise = cv2.medianBlur(fractNoise,3)
cv2.error: OpenCV(3.4.1) /io/opencv/modules/imgproc/src/smooth.cpp:4597: error: (-210)  in function medianBlur
`

reason: set theano environment variable in theano config

`echo -e "\n[global]\nfloatX=float32\n" >> ~/.theanorc`

this will set floatX to float32

## running in cluster, pyplot
`
import matplotlib
matplotlib.use('Agg') 
# Must be before importing matplotlib.pyplot or pylab for the first time!
# So must be done in the first file
import matplotlib.pyplot as plt
`
