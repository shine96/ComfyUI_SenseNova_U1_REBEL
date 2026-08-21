# ComfyUI_SenseNova_U1
[SenseNova-U1](https://github.com/OpenSenseNova/SenseNova-U1): Unifying Multimodal Understanding and Generation with NEO-Unify Architecture

# Update
* Add U1.5 (preview and official version ) support；  
* 新增U1.5（预览和正式版）支持，模型有GGUF/INT8/FP8/BF16量化，质量比之前的要好，模型缓慢上传到haggingface，也可以去我的云盘拉取  
* ~~新增fp8和convrot int8模型支持(Infographic-V3)，support fp8 and convrot int8 models~~
* ~~暂时以同步卸载模式适配moe模型,moe模式12G显存， 文生图时，count设置为8-9，图生图设置为4左右..~~
* ~~support SenseNova-U1-A3B-MoT-SFT and SenseNova-U1-A3B-MoT and SenseNova-U1-A3B-MoT-SFT-gguf ,支持A3B MOE的单体合并模型和gguf模型,快速测试可以修改节点加载repo的分割模型.~~
* ~~fix interleave some bugs ,add interleave max images number, 修复bug，交叉模式生成图片数量可以选入参，注意因为kv缓存的原因，越大越占用显存~~
* ~~support 8 steps lora now  支持 8步lora~~
* ~~Test it use 8G Vram 36G Ram ,确保内存（不是显存）大于36G~~
* ~~If Vram >16G make prefetch_count =0, 显存大于16G时，设置swap（prefetch_count）数值为0以关闭层交换（使用Q6 gguf时）~~

1.Installation  
-----
  In the ./ComfyUI/custom_nodes directory, run the following:   
```int
git clone https://github.com/smthemex/ComfyUI_SenseNova_U1
```
2.requirements  
----
```
pip install -r requirements.txt
```

3.checkpoints 
----
[8B-links](https://huggingface.co/smthem/SenseNova-U1-8B-MoT-Merger-gguf)  
[A3B-links](https://huggingface.co/smthem/SenseNova-U1-A3B-MoT-SFT-gguf)   
[U1.5-8B-links (preview and official )](https://huggingface.co/smthem/SenseNova-U1-8B-MoT-Merger-gguf)  
[A3B-links-modelscope](https://www.modelscope.cn/models/smthem/SenseNova-U1-A3B-MoT-SFT)   
[lora](https://huggingface.co/sensenova/SenseNova-U1-8B-MoT-LoRAs)  
[夸克网盘](https://pan.quark.cn/s/8180628d73c5)  
    
```
├── ComfyUI/models/gguf/
|     ├── SenseNova-U1-8B-MoT-8step-Q6_K.gguf # optional 可选
|     ├──SenseNova-U1-A3B-MoT-SFT-Q4_K_S.gguf # optional 可选
├── ComfyUI/models/diffusion_models/
|     ├── SenseNova-U1-8B-MoT-8step-merge_bf16.safetensors # optional 可选
|     ├── SenseNova-U1-A3B-MoT-SFT-merge_bf16.safetensors  可选
|     ├── SenseNova-U1-8B-MoT-Infographic-V3-int8_convrot.safetensors  可选
|     ├── SenseNova-U1-8B-MoT-Infographic-V3-fp8_scaled.safetensors  可选
├── ComfyUI/models/loras/
|     ├── SenseNova-U1-8B-MoT-LoRA-8step-V1.0.safetensors # optional 可选

```

4. Example
----
* U1.5-8B official version
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/u15_new.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/u15_new1.png)
* A3B MOE
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_a3bedit.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_a3btest.png)
* U1.0 8B
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/int8.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/fp8-v3.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_in.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_lora.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_edit.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_ti2i.png)
![](https://github.com/smthemex/ComfyUI_SenseNova_U1/blob/main/example_workflows/example_t2i.png)

5 .Citation
-----
```
@misc{sensenova2026neounify,
  title        = {NEO-unify: Building Native Multimodal Unified Models End to End},
  author       = {SenseNova},
  journal      = {Hugging Face blog},
  url          = {https://huggingface.co/blog/sensenova/neo-unify},
  year         = {2026}
}

@article{sensenova2026sensenovau1,
  title        = {SenseNova-U1: Unifying Multimodal Understanding and Generation with NEO-unify Architecture},
  author       = {Diao, Haiwen and Wu, Penghao and Deng, Hanming and Wang, Jiahao and Bai, Shihao and Wu, Silei and Fan, Weichen and Ye, Wenjie and Tong, Wenwen and Fan, Xiangyu and others},
  journal      = {arXiv preprint arXiv:2605.12500},
  year         = {2026}
}
```
