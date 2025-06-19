
# Paper-SFT: A SFT Dataset for Key Technology Identification from Scientific Literature

## Folder Structure
 <!-- 1.本数据集的50篇论文数据源以.zip形式存放。论文数据来源于中国知网。 -->
1. The dataset contains the data sources of 50 academic papers in `.zip` format. The paper data were collected from China National Knowledge Infrastructure (CNKI).
 <!-- 2.raw_data.xlsx存放的是基于先进大模型Deepseek从每篇论文中抽取的（领域，关键技术，IPC分类号）三元组，作为最终问答对的结构化描述。 -->
2. The `raw data.xlsx` file stores (field, key technology, IPC classification number) triples that are extracted from each paper by the advanced large model DeepSeek. These triples serve as the structured foundation for building the final question-answer pairs.
 <!-- 3.基于raw_data.xlsx的结构化数据，我们借用当时最为SOTA的大模型Qwen3构造领域->关键技术以及领域->IPC问答对，详见QA_Tech.jsonl以及QA_IPC.jsonl。 -->
3. Based on the structured data in `raw_data.xlsx`, we utilized the state-of-the-art large model Qwen3 at that time to generate two types of question-answer pairs: "Domain → Key Technology" and "Domain → IPC". The detailed results can be found in the files `QA_Tech.jsonl` and `QA_IPC.jsonl`.



