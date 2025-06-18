
# Description for Patents in Continuous Pre-training (CPT) Phase

<!-- CoreTech-LLM的预训练数据构建采用了来自Google Patents的权威专利文献，这一数据源的选择为模型奠定了坚实的技术语言基础。作为模型训练的核心语料，我们精心筛选了中国、美国和欧洲三大专利体系在2020-2025年间的最新专利文本，这些数据不仅代表了全球主要技术创新中心的研发成果，更蕴含着丰富的专业技术术语和产业知识图谱。这些原始数据经过严格的质量筛选，去除了低质量或信息不完整的专利文献，确保最终进入训练流程的文本都具有较高的技术含量和信息密度。具体的专利数据获取及处理过程见我们的另一个工作：CN-US-EU-JP-Patent_2020-2025。
由于每份专利数据都包含了超过20个字段，占据大量存储空间。为了适配我们的任务，我们认为并不是每个字段都是必要的，冗余字段可以去除。因而在实际的模型的增量预训练阶段，我们主要使用了"title"、"abstract"、"classifications"、"description"四个字段，其中“classifications”字段内容为该专利所涉及的国际专利分类号，用于让模型学习专利所对应的领域有哪些相关IPC分类号，从而更好地适配下游任务。-->

**CoreTech-LLM**'s pretraining data incorporates authoritative patent literature from Google Patents, establishing a robust technical linguistic foundation. The core corpus comprises carefully selected patent texts from China, US and European patent systems, representing cutting-edge R&D achievements and containing rich domain-specific terminology and industrial knowledge graphs. Through rigorous quality filtering that removed incomplete/low-quality patents, we ensured high technical value and information density in the final training data. For detailed data collection/processing methodology, see our companion work: [CN-US-EU-JP-Patent_2020-2025](https://github.com/liuquan-ustc-qmai/CN-US-EU-JP-Patent_2020-2025.git).

Each patent record contains over 20 fields that consume significant storage space. For our task, we identified redundant fields that could be removed. During incremental pretraining, we primarily utilized four key fields: "title", "abstract", "classifications" (containing IPC codes to help the model learn relevant technical domains), and "description". This selective approach optimized storage while maintaining model performance.


<!-- ## Data usage

| Classification     | Source           | Nums (Entries) | Tokens        |
|--------------------|------------------|----------------|---------------|
| General Corpus     | wudao            | 260,000        | 2,350,000,000 |
| Specialized Corpus | IPC              | 70,000         | 160,000,000   |
| Specialized Corpus | Patents          | 500,000        | 5,760,000,000 | -->



