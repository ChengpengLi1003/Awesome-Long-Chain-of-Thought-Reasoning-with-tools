# Awesome Long-Chain-of-Thought Reasoning with Tools 🤖️⛓️🛠️ (中文)


一个精选的、关于**带工具的长链思维推理 (Long Chain-of-Thought Reasoning with Tools)** 的前沿研究论文和资源的列表。

近年来，大型推理模型 (Large Reasoning Models, LRMs) 在长链思维 (Long-CoT) 方面取得了显著进展。然而，单纯依赖模型内部知识的推理过程常常导致幻觉和效率低下。为了解决这些问题，学术界和工业界开始探索将外部工具（如代码解释器、搜索引擎、API等）集成到推理过程中的方法。本仓库旨在收集和整理该领域的杰出工作，重点关注那些通过工具使用来增强模型计算、自洽性检查、信息检索和复杂任务解决能力的研究。

-----

## 目录

  - [✨ 基于提示工程与微调的方法](https://www.google.com/search?q=%23-%E5%9F%BA%E4%BA%8E%E6%8F%90%E7%A4%BA%E5%B7%A5%E7%A8%8B%E4%B8%8E%E5%BE%AE%E8%B0%83%E7%9A%84%E6%96%B9%E6%B3%95-1)
  - [🧠 基于强化学习的方法](https://www.google.com/search?q=%23-%E5%9F%BA%E4%BA%8E%E5%BC%BA%E5%8C%96%E5%AD%A6%E4%B9%A0%E7%9A%84%E6%96%B9%E6%B3%95-1)
  - [🌐 基于智能体搜索与探索的方法](https://www.google.com/search?q=%23-%E5%9F%BA%E4%BA%8E%E6%99%BA%E8%83%BD%E4%BD%93%E6%90%9C%E7%B4%A2%E4%B8%8E%E6%8E%A2%E7%B4%A2%E7%9A%84%E6%96%B9%E6%B3%95-1)

-----

## ✨ 基于提示工程与微调的方法

这类方法通过巧妙设计的提示（Hints）或者高效的微调框架，在无需大量人工标注数据的情况下，激发和训练模型使用外部工具的能力。

### START: Self-taught Reasoner with Tools

  - 📄 **论文:** [https://arxiv.org/abs/2503.04625](https://arxiv.org/abs/2503.04625)
  - 💻 **代码:** [https://github.com/ChengpengLi1003/CoRT](https://github.com/ChengpengLi1003/CoRT)
  - **摘要:** START 是一种新颖的、集成了工具的长链思维推理模型。它通过代码执行来进行复杂计算、自我检查和调试。其核心创新在于一个自学习框架，包含两个关键技术：1) **Hint-infer**：在推理时插入人工设计的提示（如“等等，这里使用Python可能是个好主意”）来激发模型使用工具的能力。2) **Hint Rejection Sampling Fine-Tuning (Hint-RFT)**：结合 Hint-infer 生成的带工具调用的推理轨迹，进行打分、过滤和修改，然后对模型进行微调。通过该框架，QwQ-32B 模型经过微调后，在多个高难度科学、数学和编程基准上取得了与最先进模型相媲美的性能。

### An empirical study on eliciting and improving r1-like reasoning models

  - 📄 **论文:** [https://arxiv.org/abs/2503.04548](https://arxiv.org/abs/2503.04548)
  - 💻 **代码:** [https://github.com/RUCAIBox/Slow\_Thinking\_with\_LLMs](https://github.com/RUCAIBox/Slow_Thinking_with_LLMs)
  - **摘要:** 这份技术报告系统性地实验和记录了影响强化学习（RL）训练的各种因素。研究表明，RL训练能够持续改进Qwen2.5-32B基础模型，提升其响应长度和测试准确率。此外，报告还探索了**工具操作 (tool manipulation)** 的使用，发现它能显著提升大型推理模型的推理性能，在AIME 2024上通过贪心搜索达到了86.67%的惊人准确率，证明了其在增强模型能力方面的有效性。

### Agentic-R1: Distilled Dual-Strategy Reasoning

  - 📄 **论文:** [https://arxiv.org/abs/2507.05707](https://arxiv.org/abs/2507.05707)
  - 💻 **代码:** [https://github.com/StigLidu/DualDistill](https://www.google.com/search?q=https://github.com/StigLidu/DualDistill)
  - **摘要:** 为解决纯文本推理和工具增强智能体各自的短板，该工作提出了 **DualDistill** 框架，将多个教师模型的互补推理策略（文本推理与工具使用）蒸馏到一个统一的学生模型中。由此训练出的 **Agentic-R1** 能够为每个查询动态选择最优策略：对算术和算法问题调用工具，对抽象问题使用文本推理。这种多策略蒸馏方法在计算密集型和标准基准测试中均提高了准确性，实现了强大而高效的推理。

### AIMO-2 Winning Solution: Building State-of-the-Art Mathematical Reasoning Models

  - 📄 **论文:** [https://arxiv.org/abs/2504.16891](https://arxiv.org/abs/2504.16891)
  - 💻 **代码:** [https://github.com/NVIDIA/NeMo-Skills](https://github.com/NVIDIA/NeMo-Skills)
  - **摘要:** 本文展示了AIMO-2竞赛的获奖方案，该方案依赖于三大支柱。首先，创建了一个名为 **OpenMathReasoning** 的大规模数据集，包含54万个高质量数学问题和320万个推理解决方案。其次，开发了一种新颖的方法，通过迭代训练、生成和质量过滤，将代码执行与推理模型相结合，最终产出170万个高质量的**工具集成推理解决方案**。第三，创建了一个名为 **GenSelect** 的流程，训练模型从多个候选中选择最有希望的解决方案，显著优于多数投票基线。该工作开源了其数据集、代码和模型，以促进后续研究。

-----

## 🧠 基于强化学习的方法

这类方法利用强化学习，通过将任务结果（如正确性、效率）作为奖励信号，让模型自主学习何时以及如何调用工具来优化其问题解决策略。

### CoRT: Code-integrated Reasoning within Thinking

  - 📄 **论文:** [https://arxiv.org/abs/2506.09820](https://arxiv.org/abs/2506.09820)
  - 💻 **代码:** [https://github.com/RUCAIBox/Slow\_Thinking\_with\_LLMs](https://github.com/RUCAIBox/Slow_Thinking_with_LLMs)
  - **摘要:** CoRT 是一个后训练框架，旨在教会大型推理模型高效地利用代码解释器（CI）。该工作通过**提示工程 (Hint-Engineering)** 来合成代码集成的推理数据，并在30个高质量样本基础上，对模型进行了监督微调、拒绝采样微调和**强化学习**。实验表明，该方法在多个挑战性数学推理数据集上取得了显著的绝对性能提升（32B模型提升4%，1.5B模型提升8%），并且大幅减少了生成所需的Token数量。

### Retool: Reinforcement learning for strategic tool use in llms

  - 📄 **论文:** [https://arxiv.org/abs/2504.11536](https://arxiv.org/abs/2504.11536)
  - **摘要:** **ReTool** 框架通过强化学习来增强模型的长程推理能力。其特点包括：1) 在自然语言推理过程中动态交织实时代码执行；2) 一个自动化的RL范式，允许模型根据结果反馈学习何时以及如何调用工具。ReTool 从合成的冷启动数据开始进行微调，随后通过RL训练，利用任务结果作为奖励来迭代优化模型的工具使用策略。在AIME基准测试中，ReTool-32B以更少的训练步数（400步）达到了67%的准确率，远超基于文本的RL基线（40%准确率，1080步），并涌现出代码自我纠正等高级行为。

### Kimi-Researcher: End-to-End Agentic RL for Autonomous Reasoning

  - 📄 **主页:** [https://moonshotai.github.io/Kimi-Researcher/](https://moonshotai.github.io/Kimi-Researcher/)
  - **摘要:** **Kimi-Researcher** 是一个擅长多轮搜索和推理的自主智能体，完全通过端到端的智能体强化学习（RL）进行训练。它在每项任务中平均执行23个推理步骤，探索超过200个URL。在极具挑战性的 **Humanity's Last Exam (HLE)** 基准测试中，它取得了26.9%的 Pass@1 分数，达到了世界领先水平。这一结果有力地证明了端到端的智能体RL能够显著提升智能体的智能水平。

-----

## 🌐 基于智能体搜索与探索的方法

这类方法构建了能够主动与外部环境（如网络、文档）交互的智能体，通过动态搜索和信息提取来弥补自身知识的不足，从而完成复杂的、知识密集型的推理任务。

### Agentic Search-Enhanced Large Reasoning Models

  - 📄 **论文:** [https://arxiv.org/abs/2501.05366](https://arxiv.org/abs/2501.05366)
  - 💻 **代码:** [https://github.com/sunnynexus/Search-o1](https://github.com/sunnynexus/Search-o1)
  - **摘要:** **Search-o1** 框架通过一种**智能体检索增强生成 (agentic RAG)** 机制来增强大型推理模型。它将一个智能体搜索工作流集成到推理过程中，使模型在遇到不确定的知识点时能够动态检索外部知识。此外，该框架还设计了一个独立的**文档内推理 (Reason-in-Documents)** 模块，用于在将信息注入推理链之前深入分析检索到的内容，以减少噪音并保持推理的连贯性。

### WebThinker: Empowering Large Reasoning Models with Deep Research Capability

  - 📄 **论文:** [https://arxiv.org/abs/2504.21776](https://arxiv.org/abs/2504.21776)
  - 💻 **代码:** [https://github.com/RUC-NLPIR/WebThinker](https://github.com/RUC-NLPIR/WebThinker)
  - **摘要:** **WebThinker** 是一个深度研究智能体，它使大型推理模型能够自主搜索网络、浏览网页，并在推理过程中起草研究报告。该框架集成了**深度网页浏览器 (Deep Web Explorer)** 模块，并采用**自主思考-搜索-起草 (Autonomous Think-Search-and-Draft)** 策略，使模型能够无缝地交织推理、信息收集和报告撰写。此外，它还通过基于RL的在线DPO策略来增强研究工具的利用。

### SciMaster: Towards General-Purpose Scientific AI Agents

  - 📄 **论文:** [https://arxiv.org/abs/2507.05241](https://arxiv.org/abs/2507.05241)
  - 💻 **代码:** [https://github.com/sjtu-sai-agents/X-Master](https://github.com/sjtu-sai-agents/X-Master)
  - **摘要:** **X-Master** 是一个旨在模拟人类研究人员的工具增强型推理智能体，它将代码概念化为一种交互语言，灵活地利用内置Python库和定制工具来增强推理。通过一个名为 **X-Masters** 的分布式、堆叠式智能体工作流，该系统性地增强了推理的广度和深度。其开源解决方案在 **HLE** 基准测试中取得了32.1%的新纪录，成为首个突破30%门槛的工作，超越了OpenAI和Google的同类研究。

### WebSailor: Navigating Super-human Reasoning for Web Agent

  - 📄 论文: https://arxiv.org/pdf/2507.02592
  - 💻 代码: https://github.com/Alibaba-NLP/WebAgent
  - 摘要: 该研究工作认为，超人智能体推理的关键在于当导航广阔信息空间时，能够系统性地减少极端不确定性。为此，论文引入了 WebSailor，一个完整的后训练方法论来灌输这种关键能力。该方法包括通过结构化采样和信息混淆生成新的高不确定性任务、RFT冷启动，以及一种高效的智能体强化学习算法——复制采样策略优化（DUPO）。WebSailor在复杂信息搜集任务中的表现显著优于所有开源智能体，达到了与闭源智能体相当的性能。

### WebDancer: Towards Autonomous Information Seeking Agency

  - 📄 论文: https://arxiv.org/pdf/2505.22648
  - 💻 代码: https://github.com/Alibaba-NLP/WebAgent
  - 摘要: 这项工作提出了一个用于构建端到端智能体信息搜集代理的统一范式。该方法包含四个关键阶段：（1）构建网页浏览数据，（2）轨迹采样，（3）用于有效冷启动的监督微调，以及（4）用于增强泛化能力的强化学习。该框架被实例化为一个名为 WebDancer 的网页智能体。在GAIA和WebWalkerQA等具有挑战性的信息搜集基准上的评估，证明了WebDancer的强大性能和该训练范式的有效性。
