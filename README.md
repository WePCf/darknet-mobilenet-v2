# Darknet for MobileNet v2

### Introduction
With the help of [MobileNet-Caffe](https://github.com/shicai/MobileNet-Caffe) and [pytorch-caffe-darknet-convert](https://github.com/marvis/pytorch-caffe-darknet-convert), the MobileNet v2 pretrained model is transferred to [darknet](https://github.com/pjreddie/darknet/tree/815293875c25774b07ec52a811793e04313e4b4a)

Only the `src/image.c` and `examples/classifier.c` are modified, search for "mobilenet" to see what are changed

### Evaluation
If you want to evaluate with single image, use

`./darknet classifier predict mobilenet/imagenet1k.data mobilenet/test.cfg mobilenet/test.weights mobilenet/cat.jpg`

Expected outputs (GPU=1, OPENCV=0):

```
19.65%: Egyptian cat
16.53%: tiger cat
10.64%: tabby
 7.38%: red fox
 6.09%: kit fox
```

If you want to validate with ILSVRC2012, please refer to [pjreddie.com](https://pjreddie.com/darknet/imagenet/) to make a valid list

The result is:

Network|Top-1|Top-5|Ops
:---:|:---:|:---:|:---:
MobileNet v2| 71.44| 90.33| 0.86Bn

### Note

- With the parameter of `predict`, the outputs will be different according to options combination in Makefile
- The network structure is not exactly same to the [paper](https://arxiv.org/abs/1801.04381), therefore the Ops is larger