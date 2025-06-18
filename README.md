
# CoreTech-LLM: A LLM focusing on key technologies and International Patent Classification(IPC) Q&A

## Introduction
 <!-- CoreTech-LLM是基于Qwen2-7B架构，通过多阶段训练流程构建的领域专用大模型。
本模型采用两阶段优化方案：
​阶段1:​增量预训练阶段​​：在精选的领域语料（涵盖国家专利局IPC及其对应描述文件、专利文本等高质量数据源）上持续训练，增强模型的基础语义理解能力；
​​阶段2:​课程学习微调阶段​​：采用渐进式课程学习（Curriculum Learning）策略，通过难度分级的监督微调，显著提升模型在技术领域的关键技术识别和IPC分类任务中的表现。 -->
**CoreTech-LLM**​ is a domain-specific LLM built upon the Qwen2.5-7B(base) architecture through a multi-stage training pipeline. The model adopts a dual-phase optimization approach:

1. Continuous Pre-training (CPT) Phase​​: Continuous training on curated domain corpora (including high-quality data sources such as IPC classification documents from national patent offices with corresponding description files, and patent texts) to enhance the model's fundamental semantic understanding capabilities.

2. Supervised FineTuning (SFT) Phase​​: Implementation of progressive Curriculum Learning (CL) strategy through difficulty-graded supervised fine-tuning, significantly improving the model's performance in technical domain tasks including key technology identification and IPC classification.


## Folder Structure
<!-- code文件夹下存放了训练所需要的所有脚本文件，包括预训练脚本、监督微调脚本、预测脚本、评估脚本以及推理脚本 -->
The **code** directory stores all necessary training scripts, covering pretraining, supervised fine-tuning, prediction, evaluation and inference.
<!-- configs文件夹下存放了使用DeepSpeed ZERO 3配置脚本 -->
The **configs** folder contains the DeepSpeed Zero-3 configuration scripts.
<!-- data文件夹下存放了训练所需要的所有数据，其中CPT-data为预训练数据（IPC含义及其描述、专利示例数据以及通用预料WUDAO数据集）；GovPatent-SFT为从国家专利局获取到的关键技术数据；Paper-SFT为从50篇论文中提取的领域-关键技术-IPC三元组。-->
The **data** folder contains all datasets required for training, structured as follows:

1. **​CPT-data**​​: Pretraining datasets, including IPC definitions and descriptions, patent sample data
and the general corpus ​​WUDAO​ (Chinese large-scale text dataset).
2. ​**GovPatent-SFT**​​: Supervised fine-tuning data of ​​key technologies​​, sourced from the National Patent Office.
3. **Paper-SFT​**​: Domain-key technology-IPC triplets extracted from ​​50 research papers​.


## Dataset
### CPT Data
| Classification     | Source           | Nums (Entries) | Tokens        |
|--------------------|------------------|----------------|---------------|
| General Corpus     | wudao            | 286,000        | 2,580,000,000 |
| Specialized Corpus | IPC              | 70,000         | 160,000,000   |
| Specialized Corpus | Patents          | 500,000        | 5,760,000,000 |




### SFT Data
| Dataset       | IPC_TASK (Train) | IPC_TASK (Test) | TECH_TASK (Train) | TECH_TASK (Test) |
|---------------|------------------|-----------------|-------------------|------------------|
| Paper-SFT     | 138              | 15              | 138               | 15               |
| GovPatent-SFT | 168              | 22              | 130               | 22               |

## Training Pipeline

### Stage 1: Continuous Pretraining
<!-- 基于qwen2.5-7b模型，在精选专利语料（含IPC分类文本、专利说明书等）上进行领域适应训练并使用WuDao通用语料进行通用能力预训练得到CoreTech-LLM-base模型。 -->
CoreTech-LLM-base is developed through domain-adaptive training on carefully selected patent corpora (including IPC-classified texts and patent specifications) based on the Qwen2.5-7B model, supplemented with WuDao general corpus for general capability pretraining.


```shell
cd /path/to/LLaMA-Factory

FORCE_TORCHRUN=1 CUDA_VISIBLE_DEVICES=0,1,2,3 \
nohup bash -c "setsid llamafactory-cli train /path/to/pretrain.yaml" \
> pretrain.log 2>&1 & \
disown -h %%
```


### Stage 2: Supervised FineTuning
<!-- 从高质量文献中以及国家专利文件中提取的领域-关键技术、领域-IPC分类问答对 -->
Based on the CoreTech-LLM-base model, the CoreTech-LLM-instruct model is obtained by using Domain-specific key technologies and domain-IPC classification Q&A pairs extracted from high-quality literature and national patent documents.

```shell
cd /path/to/LLaMA-Factory

FORCE_TORCHRUN=1 CUDA_VISIBLE_DEVICES=0,1,2,3 \
nohup bash -c "setsid llamafactory-cli train \
/path/to/run_sft.yaml" \
> sft.log 2>&1 & \
disown -h %%
```



## Install
#### Install the requirements

```markdown
git clone https://github.com/liuquan-ustc-qmai/CoreTech-LLM.git

cd CoreTech-LLM

pip install -r requirements.txt
```



## Inference
After the training is complete, now we load the trained model for local inference.

```shell
CUDA_VISIBLE_DEVICES=0 llamafactory-cli chat path/to/run_vllm.yaml

```

#### Inference Examples
To be added


## Citation
Liu, Q., Bao, H.F., & Tian, W. (2025). CoreTech-LLM: A LLM focusing on key technologies and International Patent Classification(IPC) Q&A [Software]. GitHub. https://github.com/liuquan-ustc-qmai/CoreTech-LLM


