
# GovPatent-SFT: A SFT Dataset for Key Technology Identification from China National Patent Office

## Folder Structure
 <!-- 1.本数据集的数据源来自于中国国家专利局数据，具体文件见Shared_data/2025年专利IPC分类表.zip-->
 1. The data source of this dataset comes from the China National Patent Office. The specific file is located in `Shared_data/2025年专利IPC分类表.zip`.
 <!-- 2.raw_data.csv存放了从原始文件中抽取的（领域，关键技术，IPC分类）层级化结构数据 -->
2. `raw_data.csv` stores the hierarchical structured data of (domain, key technology, IPC classification) extracted from the original files.
 <!-- 3.基于raw_data.csv，利用先进大模型Deepseek构造领域-关键技术问答对QA_Tech.jsonl文件以及领域-IPC分类问答对QA_IPC.jsonl. -->
3. Based on `raw_data.csv`, the advanced large language model DeepSeek was used to construct question-answer pairs of "domain-key technology" in the file `QA_Tech.jsonl` and "domain-IPC classification" in the file `QA_IPC.jsonl`.



