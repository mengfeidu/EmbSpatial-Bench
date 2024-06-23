# EmbSpatial-Bench
<div align="center">

<h2>🎇EmbSpatial-Bench: Benchmarking Spatial Understanding for Embodied Tasks with Large Vision-Language Models
</h2>

<div>
    Mengfei Du<sup>†</sup>;
    Binhao Wu<sup>†</sup></a>;
    Zejun Li;
    Xuanjing Huang;
    <a href='http://www.sdspeople.fudan.edu.cn/zywei/' target='_blank'>Zhongyu Wei<sup>*</sup></a>
</div>
<sup>†</sup>equal contribution; <sup>*</sup>corresponding author.


<br>

</div>


## 🍹 Overview
The recent rapid development of Large Vision-Language Models (LVLMs) has indicated their potential for embodied tasks. However, the critical skill of spatial understanding in embodied environments has not been thoroughly evaluated, leaving the gap between current LVLMs and qualified embodied intelligence unknown. Therefore, we construct EmbSpatial-Bench, a benchmark for evaluating embodied spatial understanding of LVLMs. The benchmark is automatically derived from embodied scenes and covers 6 spatial relationships from an egocentric perspective. Below are a few examples.

<img src="assets/example.png" style="width:250px" /> <img src="assets/example2.png" style="width:250px" /> <img src="assets/example3.png" style="width:250px" />




## 🍸 Dataset

### Dataset Construction
![](assets/method_overview.png)


### EmbSpatial-Bench Data
Questions from the human-verified evaluation data are formatted as multiple-choice problems. LVLMs need to select the most reasonable answer from choices. The primary metric is Accuracy. And there are two evaluation methods: generation and likelihood.
 
We share the datset in: [EmbSpatial-Bench]([https://huggingface.co/datasets/Phineas476/EmbSpatial-Bench](https://huggingface.co/datasets/Phineas476/EmbSpatial-Bench) (containing our benchmark data and sft data) for model evaluation and training.

Below shows two samples from the benchmark:
```
{
    "data_source": 'mp3d',
    "scene_id": "YVUC4YcDtcY",
    "question_id": "mp3d_57",
    "question": "From your perspective, which object in the image is at the shortest distance?",
    "relation": "close",
    "image": "/9j/4AAQ...", # base64 
    "answer_options": ['garage door', 'cabinet', 'table', 'cart'],
    "answer": 2,
    "objects": [{'name': 'garage door', 'bbox': [47, 0, 517, 254]}, {'name': 'cabinet', 'bbox': [123, 256, 130, 73]}, {'name': 'table', 'bbox': [0, 396, 640, 84]}, {'name': 'cart', 'bbox': [50, 279, 130, 138]}]
}
```

```
{
    "data_source": 'ai2thor',
    "scene_id": "FloorPlan15",
    "question_id": "ai2thor_799",
    "question": "'How are drawer and soapbottle positioned in relation to each other in the image?",
    "relation": "under",
    "image": "/9j/4AAQ...", # base64 
    "answer_options": ['The drawer is blocking the soapbottle.', 'The drawer is beneath the soapbottle.', 'The drawer is touching the soapbottle.', 'The drawer is above the soapbottle.'],
    "answer": 1,
    "objects": [{'name': 'drawer', 'bbox': [87, 223, 129, 300]}, {'name': 'soapbottle', 'bbox': [188, 73, 215, 111]}]
}
```

Below shows a sample from the EmbSpatial-SFT:

```
{
    "data_source": 'mp3d',
    "question_id": "mp3d_sft_10",
    "question": ['What is the spatial arrangement of toilet and cabinet in the image concerning each other?', 'How are toilet and cabinet positioned in relation to each other in the image?', 'In the image, how do the positions of toilet and cabinet interact with each other?', 'What is the spatial configuration between toilet and cabinet in relation to each other within the image?', 'What is the spatial relationship between toilet and cabinet in the image?'],
    "relation": "right",
    "image": "/9j/4AAQ...", # base64 
    "answer": 'The toilet is right of the cabinet.',
    "objects": [{'name': 'toilet', 'bbox': [273, 365, 86, 115]}, {'name': 'cabinet', 'bbox': [160, 413, 105, 67]}]
}
```
In order to increase the diversity of instructions, we provide a variety of questions in the sft data. For the object localization task, we randomly selected an object and its corresponding bbox from the sample for training.


## SFT with lora
We will release the sft code and model weights soon.

## 🍻 Contact

If you are interested in accessing this dataset or have any related questions, please don't hesitate to reach out to us at mfdu22@m.fudan.edu.cn.

