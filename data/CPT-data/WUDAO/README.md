
# Description for General Corpus (WUDAO) in Continuous Pre-training (CPT) Phase

 <!-- WuDao（悟道）是中国首个超大规模中文预训练数据集，由北京智源人工智能研究院主导构建。作为中文自然语言处理领域的重要基础设施，该数据集旨在为中文大模型训练提供高质量、多样化的语料支持。在CoreTech-LLM的预训练中，为了让模型在适配专用数据的同时通用能力损失最少，我们在预训练中使用WUDAO作为通用语料，平衡模型的通用能力与专用能力。-->
 <!-- wudao原始数据共200G，包含48个数据域。在实际训练过程中，我们去除了“娱乐”等与我们任务不相关的数据域，实际数据源为：博客、百科、科技、医学问答、教育、科普文章以及法律七个领域，共计286w条，约25.85亿tokens。 -->
WuDao (Wudao) is China's first ultra-large-scale Chinese pre-training dataset, led and constructed by the Beijing Academy of Artificial Intelligence. As an important infrastructure in the field of Chinese natural language processing, this dataset is designed to provide high-quality and diverse corpus support for the training of large Chinese models. In the pre-training of CoreTec-LLM, in order to minimize the loss of general capabilities while adapting to dedicated data, we use WUDAO as the general corpus in the pre-training to balance the general capabilities and dedicated capabilities of the model.
The original data of wudao totals 200G and contains 48 data fields. During the actual training process, we removed data domains such as "entertainment" that were not related to our tasks. The actual data sources were from seven fields: blogs, encyclopedias, technology, medical Q&A, education, popular science articles, and law, totaling 2.86 million entries, approximately 2.585 billion tokens.
<!-- 由于github资源管控限制，我们将完整数据上传中数据托管平台openxlab，如有需要，欢迎引用下载。 -->
Due to the resource control restrictions of github, we have uploaded the complete data to the China Data Hosting platform [openxlab](https://openxlab.org.cn/datasets/lweiranl/WUDAO). If necessary, please feel free to refer to and download it.
