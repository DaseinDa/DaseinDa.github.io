---
layout: post
title: The pure C implementation for ResNet
date: 2023-06-20 18:31:51-0401
description: The pure C implementation for ResNet
categories: CNN_C
giscus_comments: false
related_posts: true
toc:
  sidebar: right
---

## The visualization of ResNet structure

<!-- <img src="/assets/img/blogs/2023/LeNet5_C/LeNet5_Structure.jpg"  width="500">  -->

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="/assets/img/blogs/2023/ResNet_C/resnet_str.png" width="500">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">[2]</div>
</center>

I am recording my ResNet C implementation for Intel SGX usage. Because Intel SGX interfaces can only be written in pure C, even C++ would not work. Assume the dataset is MNIST, the size of the black-white image matrix is (1,28,28). The model parameters matrix number group used in the implementation is 3-dimensional. There are 4-dimensional number group in input/output matrices to record the products during the learning process. Note that each channel of the input matrix, owns an independent group of kernel, but each channel's kernel parameter update share the same total final output of this layer.

## ResNet Structure
```C

  typedef struct ResBlock1
  {
    double weight1[RES1_CHANNEL][RES1_CHANNEL][RES_LENGTH_KERNEL][RES_LENGTH_KERNEL];
    double weight2[RES1_CHANNEL][RES1_CHANNEL][RES_LENGTH_KERNEL][RES_LENGTH_KERNEL];
    double bias1[RES1_CHANNEL];
    double bias2[RES1_CHANNEL];	
  }ResBlock1;


  typedef struct ResBlock2
  {
    double weight1[RES2_CHANNEL][RES2_CHANNEL][RES_LENGTH_KERNEL][RES_LENGTH_KERNEL];
    double weight2[RES2_CHANNEL][RES2_CHANNEL][RES_LENGTH_KERNEL][RES_LENGTH_KERNEL];	
    double bias1[RES1_CHANNEL];
    double bias2[RES1_CHANNEL];	
  }ResBlock2;	


  typedef struct Res1_Feature
  {
    double input_pad[RES1_CHANNEL][14][14];
    double conv1[RES1_CHANNEL][12][12];

    double conv1_pad[RES1_CHANNEL][14][14];
    double conv2[RES1_CHANNEL][12][12];
  }Res1_Feature;

  typedef struct Res2_Feature
  {
    double input_pad[RES2_CHANNEL][6][6];
    double conv1[RES2_CHANNEL][4][4];
    double conv1_pad[RES2_CHANNEL][6][6];
    double conv2[RES2_CHANNEL][4][4];
  }Res2_Feature;



  typedef struct ResNet
  {
    double weight1[INPUT][LAYER1][LENGTH_KERNEL][LENGTH_KERNEL];//Layer1 kernel
    //maxpool
    ResBlock1 res1;
    double weight2[LAYER1][LAYER2][LENGTH_KERNEL][LENGTH_KERNEL];//Layer2 Kernel
    //maxpool
    ResBlock2 res2;

    double fc[512][OUTPUT];


    double bias1[LAYER1];
    double bias2[LAYER2];


    double bias_fc[OUTPUT];

  }ResNet;

```

## ResNet implementation
```C
#define CONVOLUTION_RES_FORWARD(res_input,input,output,weight,bias,action)		\
{																				\
	for (int x = 0; x < GETLENGTH(weight); ++x)									\
		for (int y = 0; y < GETLENGTH(*weight); ++y)							\
			CONVOLUTE_VALID(input[x], output[y], weight[x][y]);					\
	FOREACH(i, GETCOUNT(output))												\
		((double*)output)[i] += ((double*)res_input)[i];							\
	FOREACH(j, GETLENGTH(output))												\
		FOREACH(i, GETCOUNT(output[j]))											\
		((double *)output[j])[i] = action(((double *)output[j])[i] + bias[j]);	\
}
#define ResBlock_Forward(input,output,res,action)								\
{																				\
	PADDING_fill(output.input_pad,input);										\
	CONVOLUTION_FORWARD(output.input_pad,output.conv1,res.weight1,res.bias1,action);\
	PADDING_fill(output.conv1_pad,output.conv1);								\
	CONVOLUTION_RES_FORWARD(input, output.conv1_pad,output.conv2,res.weight2,res.bias2,action);\
}																					\
#define ResBlock_Backward(res,res_error,res_weight,res_deltas,actiongrad)	\
{																			\
	CONVOLUTION_BACKWARD(res.conv1_pad, res_error.conv1_pad,res_error.conv2,res_weight.weight2,res_deltas.weight2,res_deltas.bias2,actiongrad);\
	PADDING_remove(res_error.conv1,res_error.conv1_pad);											\
	CONVOLUTION_BACKWARD(res.input_pad, res_error.input_pad,res_error.conv1,res_weight.weight1,res_deltas.weight1,res_deltas.bias1,actiongrad);\
}
```

## Questions that should make a attention during the implementation

* learning_rate=10 would cause gradient dissapearance
* 1/300*x would cause gradient dissappearance in comparison with x/300;
* The learning_rate=0.5 would also cause gradient lost, should set = 0.1
