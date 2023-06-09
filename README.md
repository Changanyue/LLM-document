
# Intro
采用BART结构，使用Swin Transformer做图像encoder，ChatGLM做文本decoder，将文本和图像表征做cross-attention。模型可以完成OCR，文档内容理解，文档信息抽取等文档智能任务。参考[`Donut`]([https://huggingface.co/datasets/naver-clova-ix/synthdog-zh](https://github.com/clovaai/donut))


## Dataset
通过文本构建含有文本的图像，同时添加一些噪声。
采用如下数据进行训练：

- [`synthdog-zh`](https://huggingface.co/datasets/naver-clova-ix/synthdog-zh): Chinese, 0.5M.



## 训练
以OCR的方式进行预训练，让模型输出图片对应文字




### Train

```bash
CUDA_VISIBLE_DEVICES="1" python my_models/swin_gpt2/train.py --config my_models/config/train_synthdog_gpt2.yaml --exp_version "donut_gpt2_pretrain_exp_0"

```

### Test

```bash
CUDA_VISIBLE_DEVICES="0" python my_models/swin_gpt2/test.py --config my_models/config/infer_synthdog_gpt2.yaml 

```


## swin_chatglm

```bash
CUDA_VISIBLE_DEVICES="0" python my_models/swin_chatglm/train.py --config my_models/config/train_synthdog_gpt2.yaml --exp_version "donut_chatglm_pretrain_exp_0"





```



```
