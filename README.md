[人员](#人员) | [赞助](#赞助) | [引用](#引用)

# 丝绸之路: 构建中文大语言模型的数据基础

丝绸之路是骆驼项目的数据仓库页面。展示了骆驼项目中使用和发布的数据集。

丝绸之路是[Luotuo(骆驼)](https://github.com/LC1332/Luotuo-Chinese-LLM)的子项目之一, 后者由李鲁鲁, 冷子昂, 陈启源发起。

<p align="center">
    <img src="https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/image/icon_silk_road.png" height="250">
</p>

+ If you find this helpful, please star our major repo [Luotuo(骆驼)](https://github.com/LC1332/Luotuo-Chinese-LLM), Thanks Very Much

+ 如果你感到这个页面对你有帮助，拜托您去我们[骆驼的主页](https://github.com/LC1332/Luotuo-Chinese-LLM)也点上star，非常感谢！另外对于数据的需求，也尽量去主项目页提issue，谢谢。


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

https://huggingface.co/datasets/silk-road/Wizard-LM-Chinese-instruct-evol


```python
from datasets import load_dataset

dataset = load_dataset("silk-road/Wizard-LM-Chinese-instruct-evol")
```

Chinese-WizardLM是在MSRA的Wizard-LM数据集上，对指令进行翻译，然后再调用GPT获得答案的数据集

Wizard-LM包含了很多难度超过Alpaca的指令。

中文的问题翻译会有少量指令注入导致翻译失败的情况.

中文回答是根据中文问题再进行问询得到的。

### 更多的指令数据集

在训练[迷你骆驼](https://github.com/LC1332/Mini-Luotuo)的时候，我们参考PandasLLM和HuggingFace，合并了15M的指令数据。我们正在研究这部分数据是否可以用合适的方式发布出来。


---

## 阅读理解数据

阅读理解数据包含story-questions-answers的组合。

### Chinese-CoQA

https://huggingface.co/datasets/silk-road/Luotuo-QA-A-CoQA-Chinese

Chinese-CoQA是在CoQA上进行的中文翻译和增广。使用这个数据集需要签署协议。

```python
from datasets import load_dataset

# If the dataset is gated/private, make sure you have run huggingface-cli login
dataset = load_dataset("silk-road/Luotuo-QA-A-CoQA-Chinese")
```

CoQA中的文本来自七个不同领域的段落：儿童故事、文学作品、中学和高中英语考试、新闻、维基百科、Reddit和Science。

CoQA数据集经过简单清洗，共有7012个story，我们在此基础上将整个数据集翻译成了中文并进行了增广，其中每个story中包含5个左右的问题，每个问题进行了5次增广。

我们的协议与CoQA数据集原始协议保持一致，请阅读以下内容。

CoQA数据集包含来自七个领域的段落。我们将其中五个领域的段落以以下许可证公开：

文学和维基百科段落遵循CC BY-SA 4.0许可证共享。 儿童故事选自MCTest，该数据集附带MSR-LA许可证。 中学/高中考试段落选自RACE，该数据集有自己的许可证。 新闻段落选自DeepMind CNN数据集，该数据集有Apache许可证。


### Luotuo-QA-B

https://huggingface.co/datasets/Logic123456789/luotuoQA-B

Luotuo-QA-B是一个增广的阅读理解问题。

```python
from datasets import load_dataset

# If the dataset is gated/private, make sure you have run huggingface-cli login
dataset = load_dataset("Logic123456789/luotuoQA-B")
```

我们的数据集是在3个开源数据集之上生成构建的，这3个数据集分别是：

- Chinese Scientific Literature Dataset

- CNN-DailyMail News Text Summarization

- arXiv Dataset

我们在这些数据集的基础上针对每一个摘要或新闻生成了5个“问题-答案”对。数据分布如下：

-从Chinese Scientific Literature Dataset(CSL)数据集中生成了25836条中文数据，共129180个问答对。

-从CNN-DailyMail News Text Summarization数据集中生成了2026条数据，共10130个问答对。

-从arXiv Dataset数据集中生成了3602条英文数据，共18010个问答对。

此外，由于此数据集是我们[Luotuo-QA](https://github.com/LC1332/Luotuo-QA)项目的一部分，我们将它命名为luotuo-QA-B。


---

## 图文跨模态数据


### Chinese-MMC4-130k

https://huggingface.co/datasets/silk-road/MMC4-130k-chinese-image

MMC4-130k-chinese是对MMC4中，抽样了130k左右 simliarty较高的图文pair得到的数据集

并对这里所有的caption进行了翻译。由于这批抽样是MMC4上CLIP-L-14 similarity较高响应的图片，响应普遍都在0.4及以上。

怀疑OpenAI CLIP训练的时候，大量使用了图内带文字的图片。

### Chinese-Coco-Captioning

[Coming Soon]

Chinese-Coco-Captioning是对CocoCaption进行了翻译

我们翻译了包括Coco-2017的训练集以及若干个其他年份的Validation集合。

这部分数据正在整理，将在之后发布

---

## Embedding蒸馏数据

### CNewSum-Embedding

[Coming Soon]

CNewSum-Embedding是我们在训练[骆驼嵌入](https://github.com/LC1332/Luotuo-Text-Embedding)时使用的数据

对235k的中文新闻数据，实行了断句成为前后文。并且对于前后文分别求了OpenAI的1536维的Embedding特征。

这部分数据正在整理，将在之后发布

---


## 人员

<a name="赞助"></a>

## 赞助(Sponsorship) 骆驼项目

丝绸之路中的数据翻译费用完全使用了募集的捐款，感谢大家对我们项目的支持！

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
