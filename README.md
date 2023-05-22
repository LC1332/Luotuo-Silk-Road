[赞助](#赞助) | [引用](#引用)

# 丝绸之路: 构建中文大语言模型的数据基础

丝绸之路是骆驼项目的数据仓库页面。展示了骆驼项目中使用和发布的数据集。

丝绸之路是[Luotuo(骆驼)](https://github.com/LC1332/Luotuo-Chinese-LLM)的子项目之一, 后者由李鲁鲁, 冷子昂, 陈启源发起。

<p align="center">
    <img src="https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/image/icon_silk_road.png" height="250">
</p>

骆驼项目发起至今，主要涉及以下几类数据

- [对话与指令数据集](#对话与指令数据集)
    - [Luotuo-Chinese-Alpaca](#Luotuo-Chinese-Alpaca)
    - [Chinese-Dolly](#Chinese-Dolly)
    - [Chinese-WizardLM](#Chinese-WizardLM)
- [阅读理解数据](#阅读理解数据)
    - [Chinese-CoQA](#Chinese-CoQA)
    - [Luotuo-QA-B](#Luotuo-QA-B)
- [图文跨模态数据](#图文跨模态数据)
    - [Chinese-MMC4-130k](#Chinese-MMC4-130k)
    - [Chinese-Coco-Captioning](#Chinese-Coco-Captioning)
- [Embedding蒸馏数据](#Embedding蒸馏数据)
    - [CNewSum-Embedding](#CNewSum-Embedding)


---

## 对话与指令数据集


### Luotuo-Chinese-Alpaca

https://huggingface.co/datasets/silk-road/Vanilla-chinese-alpaca-luotuo

Chinese-Alpaca是我们在3月21日启动骆驼项目时候最早使用的数据集。包含了斯坦福Alpaca的翻译数据（有丢失）。

并且由于当时使用了较为初级的翻译指令，对于指令翻译会有“注入”的现象，会引入一定的噪音

Hugging Face使用方式:

```python
from datasets import load_dataset

dataset = load_dataset("silk-road/Vanilla-chinese-alpaca-luotuo")
```

如果你希望更好的翻译方式，请查看更好的翻译脚本 <a href="https://colab.research.google.com/github/LC1332/Luotuo-Chinese-LLM/blob/main/notebook/improvedTranslation.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a> 

如果你希望质量更好的指令数据集，请查看后文的Chinese-WizardLM和Chinese-Dolly

### Chinese-Dolly

https://huggingface.co/datasets/silk-road/chinese-dolly-15k

```python
from datasets import load_dataset

dataset = load_dataset("silk-road/chinese-dolly-15k")
```

Chinese-Dolly-15k是骆驼团队翻译的Dolly instruction数据集。

原数据集'databricks/databricks-dolly-15k'是由数千名Databricks员工根据InstructGPT论文中概述的几种行为类别生成的遵循指示记录的开源数据集。这几个行为类别包括头脑风暴、分类、封闭型问答、生成、信息提取、开放型问答和摘要。

翻译后的数据包含完整的中英文对照的context和instruction字段，并且还有问题所属的category。

### Chinese-WizardLM


### 更多的指令数据集

在训练[迷你骆驼](https://github.com/LC1332/Mini-Luotuo)的时候，我们参考PandasLLM和HuggingFace，合并了15M的指令数据。我们正在研究这部分数据是否可以用合适的方式发布出来。


---

## 阅读理解数据

### Chinese-CoQA

### Luotuo-QA-B

---

## 图文跨模态数据


### Chinese-MMC4-130k

---

## Embedding蒸馏数据


### CNewSum-Embedding

---

<a name="赞助"></a>

## 赞助(Sponsorship) 骆驼项目

如果你有兴趣赞助骆驼项目，请点击[主项目](https://github.com/LC1332/Luotuo-Chinese-LLM#%E8%B5%9E%E5%8A%A9sponsorships)或者查看[赞助表单](https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/data/Sponsorship_and_balance.md)

If you are interested in sponsoring the [Luotuo Project](https://github.com/LC1332/Luotuo-Chinese-LLM#%E8%B5%9E%E5%8A%A9sponsorships), please click on the [major project](https://github.com/LC1332/Luotuo-Chinese-LLM) or view the [sponsorship form](https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/data/Sponsorship_and_balance.md).

[回到开头](#BigTitle)


## 引用

如果您在项目中使用了我们的模型、代码或者数据，请引用这个repo。

```
@misc{alpaca,
  author={Ziang Leng, Qiyuan Chen and Cheng Li},
  title = {Luotuo: An Instruction-following Chinese Language model, LoRA tuning on LLaMA},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/LC1332/Luotuo-Chinese-LLM}},
}
```
