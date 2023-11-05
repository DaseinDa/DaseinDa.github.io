---
layout: post
title: The pure C implementation for Transformer
date: 2023-11-01 18:31:51-0401
description: The pure C implementation for Transformer
categories: CNN_C
giscus_comments: false
related_posts: true
toc:
  sidebar: right
---

## The visualization of Tansformer structure


<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="/assets/img/blogs/2023/Transformer_C/transformer_str.jpg" width="500">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">[1]</div>
</center>

## Vision Transformer
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="/assets/img/blogs/2023/Transformer_C/vit.jpg" width="500">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">[2]</div>
</center>

### Code for ViT's matrix to patchs
```C
    #define Feature2Patch(input,output)											\
    {																			\
        size_t image_size = GETLENGTH(*input);									\	
        size_t patch_size=GETLENGTH(**output);									\
        size_t patch_num_row = image_size/patch_size;							\		
        FOREACH(o0, GETLENGTH(output))											\
            FOREACH(o1, GETLENGTH(output))										\
                FOREACH(o2, GETLENGTH(output))									\
                    FOREACH(o3, GETLENGTH(output))								\
                        output[o0][o1][o2][o3]=input[o1][o0/patch_num_row*patch_size+o2][o0%patch_num_row*patch_size+o3];\
    }

    for(int i=0;i<28;i++){
	    for(int j=0;j<28;j++){
			features.input[0][i][j]=i*28+j;
		}
	}
	printf("###########%d\n",features.input[0][1][2]);
	Feature2Patch(features.input, features.input_patch);
	for(int i=0;i<PATCH_NUM;i++){
		for(int j=0;j<PATCH_SIZE;j++){
			printf("\n");
			for(int k=0;k<PATCH_SIZE;k++){
				printf("output[%d][0]%d[%d] is %f  ", i,j,k,features.input_patch[i][0][j][k]);
			}
		}
		printf("\n");
		sleep(2);
	}

```
I am recording my Transformer C implementation for Intel SGX usage. Because Intel SGX interfaces can only be written in pure C, even C++ would not work. Assume the dataset is MNIST, the size of the black-white image matrix is (1,28,28). The model parameters matrix number group used in the implementation is 3-dimensional. There are 4-dimensional number group in input/output matrices to record the products during the learning process. Note that each channel of the input matrix, owns an independent group of kernel, but each channel's kernel parameter update share the same total final output of this layer.

## Reference
<div id="refer-anchor-1"></div>

- [1] https://arxiv.org/pdf/1706.03762.pdf

<div id="refer-anchor-1"></div>

- [2] https://arxiv.org/pdf/2010.11929.pdf

