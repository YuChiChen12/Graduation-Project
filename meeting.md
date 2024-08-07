# Graduation-Project
## Benchmark Paper
1. [Financial time series forecasting with multi-modality graph neural network](https://www.sciencedirect.com/science/article/pii/S003132032100399X) [Github](https://github.com/finint/MAGNN/tree/main)
2. [NExT-GPT: Any-to-Any Multimodal LLM](https://ar5iv.labs.arxiv.org/html/2309.05519) [NExT-GPT:Any-to-Any Multimodal Large Language Model](https://next-gpt.github.io/)
3. [StructGPT: A General Framework for Large Language Model to Reason over Structured Data](https://ar5iv.labs.arxiv.org/html/2305.09645) [Github](https://github.com/RUCAIBox/StructGPT)
## 0616 Proposed Idea - M-RAGNN(Multimodal Retrieval-Augmented Graph Neural Network for Financial Forecasting) (Two Stages)
1. 對 LLM 做 prompt engineering & fine-tune
   > 可參照
   > [AlphaFin: Benchmarking Financial Analysis with Retrieval-Augmented Stock-Chain Framework](https://arxiv.org/abs/2403.12582)
   > [內文](https://arxiv.org/html/2403.12582v1)
   > [Github](https://github.com/AlphaFin-proj/AlphaFin)
   * RAG
2. 將新聞透過 LLM 分析並整理
3. 利用兩種輸入(股價&新聞分析)建構出 multi-modality graph neural network (考慮到股票的潛在相互依賴性 & lead-lag effect)
   > 可參照
   > [Financial time series forecasting with multi-modality graph neural network](https://www.sciencedirect.com/science/article/pii/S003132032100399X)
   > [Github](https://github.com/finint/MAGNN)
   > * 神经开放域信息抽取OpenIE
   > * 探索OpenIE：一个强大的开放信息提取工具
   > * OpenNRE：可一键运行的开源关系抽取工具包
   > * 机器学习 Micro-F1和Macro-F1详解
* 未來展望
   * 分為對總經/產業/個股影響
      * 利用 multihead attention layer 整合三者的互相影響
   * 用 self reflection 優化模型的解釋和預測
## 進度規劃
### Jun. => 實驗設計 & 參考 benchmark paper
### Jul. => Prediction with LLM
### Aug. => Prediction with LLM & MAGNN
### Sep. => MAGNN & Two Stages
### Oct. => Two Stages
### Nov. => 總結實驗結果
### Dec. => 成果發表

## 0602 Proposed Idea
* [Incorporating Pre-trained Model Prompting in Multimodal Stock Volume Movement Prediction](https://arxiv.org/abs/2309.05608)
* [ChatGPT Informed Graph Neural Network for Stock Movement Prediction](https://arxiv.org/abs/2306.03763)
* [Stock Movement Prediction with Multimodal Stable Fusion via Gated Cross-Attention Mechanism](https://arxiv.org/abs/2406.06594)
* Leveraging hierarchical language models for aspect-based sentiment analysis on financial data
  * 更多層 hierarchical
  * 針對不同的產業選擇不同的 aspect
  * 測試其他 few-shot learning 的結果
  * A Hybrid Approach To Aspect Based Sentiment Analysis Using Transfer Learning，利用他的方法強化 ABSA 效果(？
  * LM用較新的
* Time LLM
  * 將 timellm 用於 stock return prediction
  * 更改或強化 patch reprogramming 的方式
    * 利用像 stockformer STL的分割方式
    * 生成更好的 prompt
    * vs. TimeGPT
      * TimeGPT retrain model 需要大量的時間算力以及數據
      * TimeGPT 只能使用在單一領域
      * 方法截然不同但結果相似
* Stockformer
  * 將 Stockformer 模型分為三個子模塊，分別處理趨勢、季節性和殘差組件。將股價透過 STL decomposition 分解成 trend, seasonal, and residual 三個 components 
    * [时间序列的数据分析(四):STL分解](https://aitechtogether.com/python/59882.html)
    * [STL: A Seasonal-Trend Decomposition Procedure Based on Loess 中文筆記與python套件](https://medium.com/@a0922/stl-a-seasonal-trend-decomposition-procedure-based-on-loess-%E4%B8%AD%E6%96%87%E7%AD%86%E8%A8%98%E8%88%87python%E5%A5%97%E4%BB%B6-190228b9c700)
    * [时间序列分解论文STL: A Seasonal-Trend Decomposition Procedure Based on Loess](https://blog.csdn.net/qq_44384577/article/details/109222247)
    * 使用多頭自注意力機制，使模型能夠關注不同特徵對這三個組件的不同影響
  * 多模態特徵：利用文本分析強化 encoder 的解釋性
    * 將文本數據轉換為數值特徵，並使用多模態學習技術，整合文本特徵與時間序列數據
    * 為每個子模塊輸入不同的特徵組合。例如，趨勢模塊可以更多地關注長期新聞和財報數據，而季節性模塊則可以重點關注周期性事件和數據
  * 在 decoder 後面加入可解釋的方法
  * 強化學習優化
    * 解釋部分可利用 [self reflection](https://arxiv.org/abs/2303.11366) 優化 (每次預測後，將預測結果與實際結果進行比較，生成反思回饋)
    * 使用PPO算法根據反思回饋更新模型參數，使其能夠更準確地預測趨勢、季節性和殘差組件
  * 不同行業選擇不同特徵(？
   
   > [Temporal Graph Networks for Deep Learning on Dynamic Graphs](https://arxiv.org/abs/2006.10637)
   > [Content](https://ar5iv.labs.arxiv.org/html/2006.10637)
   > [Github](https://github.com/twitter-research/tgn?utm_source=catalyzex.com)
   > [Video](https://www.youtube.com/watch?v=W1GvX2ZcUmY)

## 0621 Proposed Idea
### LLM & KG Overview
* [Unifying Large Language Models and Knowledge Graphs: A Roadmap](https://arxiv.org/abs/2306.08302)
   * [Content](https://ar5iv.labs.arxiv.org/html/2306.08302)
   * [论文阅读：Unifying Large Language Model and Knowledge Graph：A RoadMap](https://www.cnblogs.com/zjz2333/p/17780118.html)
   * [LLM+KGs综述：Unifying Large Language Models and Knowledeg Graphs: A Roadmap](https://blog.csdn.net/weixin_52953225/article/details/131456764)
### Proposed
* KG-enhanced LLMs：KG-enhanced LLM inference
* Synergized LLMs + KGs：LLMs as Agents Reasoning
### Benchmark - Synergized LLMs + KGs
* [StructGPT: A General Framework for Large Language Model to Reason over Structured Data](https://arxiv.org/abs/2305.09645)
   * [Content](https://ar5iv.labs.arxiv.org/html/2305.09645)
   * [Github](https://github.com/RUCAIBox/StructGPT)
   * [Video](https://aclanthology.org/2023.emnlp-main.574.mp4)
* [Complex Logical Reasoning over Knowledge Graphs using Large Language Models](https://arxiv.org/abs/2305.01157)
   * [Content](https://ar5iv.labs.arxiv.org/html/2305.01157)
   * [Github](https://github.com/Akirato/LLM-KG-Reasoning?utm_source=catalyzex.com)
* [Think-on-Graph: Deep and Responsible Reasoning of Large Language Model on Knowledge Graph](https://arxiv.org/abs/2307.07697)
   * [Content](https://ar5iv.labs.arxiv.org/html/2307.07697)
   * [Github](https://github.com/IDEA-FinAI/ToG)
### Benchmark - KG
* [FinDKG: Dynamic Knowledge Graph with Large Language Models for Global Finance](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4608445)
   * [FinDKG Website](https://xiaohui-victor-li.github.io/FinDKG/)
   * [Github](https://github.com/xiaohui-victor-li/FinDKG)
* [Temporal-Relational hypergraph tri-Attention networks for stock trend prediction](https://www.sciencedirect.com/science/article/pii/S0031320323004570)
   * [Github](https://github.com/lixiaojieff/HGTAN)
### Other References
[Github KG-LLM-Papers](https://github.com/zjukg/KG-LLM-Papers)
> [Temporal and Heterogeneous Graph Neural Network for Financial Time Series Prediction](https://arxiv.org/abs/2305.08740)
> [Content](https://ar5iv.labs.arxiv.org/html/2305.08740)
> [Github](https://github.com/finint/THGNN/tree/main)
