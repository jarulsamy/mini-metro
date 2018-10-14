
# m0
ssd_mobilenet_v1 with default parameters
achieves mAP ~0.16 after 100 steps
overfitting after 100 steps

# m1
ssd_mobile_net_v1 with only one box shape (square) and only one feature map 
feature map is highest layer in network used in default with smallest default boxes
gave a similar mAP ~0.16 after around 0.75 so trains a bit faster and produces a smaller model

# m1-2
m1 reduce scales to 0.05
no improvement over m1

# m1-3
m1 reduce scales to 0.05 and add additional aspect ratio at 0.7 which will be more "square" on original image (before it is reduced to 300x300)
no improvement over m1

# m2
same as m0 but trained on forked install
trained multiple times to ensure consistency and it appears to be stable 

# m2-1
same as m2 but using a 3x3 kernel (filter) size instead of the default 1x1
mAP peaked at ~0.10 after 70 steps but did not appear to give any noticeable uplift (probably because our targets are not large enough to exceed the focal area of a 1x1 kernal on even the lowest layer)

# m2-2
m2 with random horizontal flip activated
mAP ~0.2 after 80 steps


# m3
ssd_mobilenet_v1_fpn with default parameters
this has a higher input resolution (640x640) and uses feature pyramic network
the fpn should improve performance on small objects
training is very slow, cannot use batch greater than 20 due to memory (20 is same as previous attempts anyway)
trains around 2 steps per 20 mins compared to ~13 for non-fpn version
after 100 steps the mAP is up and down
test loss does not decrease consistently and no predicted boxes

# m4
m2 with depth multiplier set to 0.75 to check if mobilenet layers are affected

# m5
m2 with training data also used for evaluation
the api restricts us to evaluating both train/test when in eval only mode 

# m6
m2 config, but with paths set for training on google cloud colab notebook

# m6-1
m3 config, but with paths set for training on google cloud colab notebook



