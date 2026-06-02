# ComfyUI_LongCat_Avatar
[LongCat_Avatar](https://github.com/meituan-longcat/LongCat-Video),an upgraded open-source framework for audio-driven human video generation.

Update
----
* 新增whisper-large-v3 原生加载节点，总感觉对comfyUI的音频解码有问题，可能是错觉
* use comfyUI whisper-large-v3 audio_encoders，offload lora to cpu
* 音频解码改成comfyUI内置单体模型方式，开启lora和cache的卸载，降低显存占用
* 部署节点，目前单人和双人测试通过，部分参数未严谨测试，请自行测试，有bug可以提issues或反馈给我的B站或小红书smthem账号

1.Installation  
----
  In the ./ComfyUI/custom_nodes directory, run the following:   
```
git clone https://github.com/smthemex/ComfyUI_LongCat_Avatar
```
2.requirements  
----
```
pip install -r requirements.txt
```
3.checkpoints 
----
  
huggingface links: [dit-int8](https://huggingface.co/smthem/LongCat-Video-Avatar-1.5-merge)  
huggingface links: [text_encoders](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/tree/main/split_files/text_encoders)  
huggingface links: [vocal_separator/whisper-large-v3/lora](https://huggingface.co/meituan-longcat/LongCat-Video-Avatar-1.5/tree/main)   
huggingface links: [vae](https://huggingface.co/meituan-longcat/LongCat-Video ) 

```
├── ComfyUI/models/diffusion_models/
|     ├── LongCat-Video-Avatar-1.5-int8.safetensors
├── ComfyUI/models/loras/
|     ├── LongCat_Avatar_1.5_lora.safetensors
├── ComfyUI/models/vae/
|     ├── LongCat_Avatar_1.5_vae.safetensors
├── ComfyUI/models/clip/
|     ├── umt5_xxl_fp8_e4m3fn_scaled.safetensors
├── ComfyUI/models/audio_encoders/
|     ├── whisper-large-v3.safetensors # rename or not 
├── ComfyUI/models/longcat/ 
|     ├── Kim_Vocal_2.onnx # 配套config文件会自动下，可以下了先放进去

```

4 Example
----

![](https://github.com/smthemex/ComfyUI_LongCat_Avatar/blob/main/example_workflows/example.png)

5 Citation
----

```
@misc{meituanlongcatteam2025longcatvideotechnicalreport,
      title={LongCat-Video Technical Report}, 
      author={Meituan LongCat Team and Xunliang Cai and Qilong Huang and Zhuoliang Kang and Hongyu Li and Shijun Liang and Liya Ma and Siyu Ren and Xiaoming Wei and Rixu Xie and Tong Zhang},
      year={2025},
      eprint={2510.22200},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2510.22200}, 
}
@misc{meituanlongcatteam2025longcatvideoavatar15technicalreport,
      title={LongCat-Video-Avatar 1.5 Technical Report}, 
      author={Meituan LongCat Team},
      year={2026},
      eprint={},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={}, 
}
@misc{meituanlongcatteam2025longcatvideoavatartechnicalreport,
      title={LongCat-Video-Avatar Technical Report}, 
      author={Meituan LongCat Team},
      year={2025},
      eprint={},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={}, 
}
```
