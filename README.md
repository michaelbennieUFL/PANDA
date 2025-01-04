# PANDA – Paired Anti-hate Narratives Dataset from Asia
Using an LLM-as-a-Judge to Create the First Chinese Counterspeech Dataset

---
## 📜 Paper

The pre-print discussing the methodology of this project and data analysis can be found here: https://arxiv.org/abs/2501.00697.

### 📜 Contact and Feedback

Please direct any questions or feedback to:

- **Michael Bennie** – [michaelbennie@ufl.edu](mailto:michaelbennie@ufl.edu)  
- **Demi Zhang** – [zhang.yidan@ufl.edu](mailto:zhang.yidan@ufl.edu)

We welcome suggestions and contributions to improve **PANDA** and advance the research on Chinese counterspeech!

---


## ❗️ Disclaimer
Please be aware that the **PANDA** dataset contains explicit content, including hateful and offensive remarks, which may be upsetting or triggering. The material provided is for **research purposes only** and should be handled responsibly and ethically.

1. **No Endorsement**: The presence of hateful content within the dataset does **not** reflect the views or opinions of the authors or any affiliated institutions.
2. **Intended Use**: The dataset is primarily intended for NLP research on **hate speech detection**, **counterspeech generation**, **content moderation**, and **social impact analysis**.
3. **Ethical Handling**: By using this dataset, the onus is on you to handle the data with due care, respecting individual privacy and dignity, and to avoid misuse or propagation of hateful language.

---

## 📜 Why PANDA?
While Chinese is one of the most widely spoken languages globally, **publicly available resources for Chinese counterspeech are extremely scarce**. To address this gap, **PANDA** offers:
1. **The first Mandarin Chinese dataset** that pairs hate speech (HS) and **automatically + human-curated counterspeech (CS)** responses.  
2. **Context-rich annotations** from multiple open-source Chinese hate speech datasets, combined with newly generated counterspeech.  
3. **Human Labled Hate speech** data from previous hate speech datasets were rescored by humans for more accurate results.

---

## 📜 Dataset Overview
- **Total HS–CS Rows**: 785  
- **Language**: Simplified Chinese (with some code-switched English in certain cases)  
- **Sources of Hate Speech**:  
  - **COLD** [(Zhang et al., 2020)](https://github.com/link/to/cold)  
  - **SWSR** [(Li et al., 2021)](https://github.com/link/to/swsr)  
  - **CHSD** [(Wu et al., 2022)](https://github.com/link/to/chsd)  

These sources were chosen for their open-source availability and coverage of various hate/offensive scenarios, such as **sexism**, **racism**, **regional bias**, **anti-LGBTQ**, and **general offensive content**.

### Dataset Structure
The dataset is provided as a single CSV file named `panda_dataset.csv`, consisting of the following columns:

| **Column Name**          | **Description**                                                                |
|--------------------------|--------------------------------------------------------------------------------|
| `hatespeech`             | The input text being evaluated for hateful or problematic content.             |
| `hateScore`              | Counterspeech: -1; Neutral or Ambiguous: 0; Hate Speech: 1                     |
| `userEnteredResponse`    | The human entered response addressing the content of the `hatespeech`.      |
| `generatedResponse1`     | The first AI-generated response to the `hatespeech` text.                      |
| `generatedResponse2`     | The second AI-generated response to the `hatespeech` text.                     |
| `generatedResponse3`     | The third AI-generated response to the `hatespeech` text.                      |
| `generatedResponse4`     | The fourth AI-generated response to the `hatespeech` text.                     |


Generated responses 1-4 are ordred by the JudgeLM score they recived from a round robin tournament comparing each AI generated answer.
As such, `generatedResponse1` would be the most prefered AI answer by JudgeLM and `generatedResponse4` would be the least perfered of the 4.

---

## 📜 How the Dataset Was Created
1. **Data Collection**: We aggregated hateful/offensive posts from the above-mentioned **open-source** Chinese datasets.  
2. **Pre-filtering**: We applied an LLM-based scoring to isolate texts that are likely to be hate speech, refining them based on length and predicted toxicity.  
3. **Counterspeech Generation**: We used a **simulated annealing** method with multiple LLMs to generate 4 distinct CS responses for each HS instance.  
4. **Round-Robin Ranking**: A specialized LLM-as-a-Judge (JudgeLM) scored these CS responses in a pairwise, round-robin manner, and we preserved final ranks.  
5. **Human Annotation**: Human reviewers then selected the best CS from the 4 candidates, optionally revised it for accuracy and fluency, and labeled each final pair.  

**Important Note**: Despite this multi-layer curation process, there may still be edge cases or subjective instances in which the line between hateful speech and other forms of negativity is blurred.

---

## 📜 Usage
- **Hate Speech Detection Research**: Train or fine-tune classification models to detect specific hateful content in Chinese.
- **Counterspeech Modeling**: Fine-tune or evaluate generative models that produce context-sensitive counterspeech in Chinese.
- **Behavioral/Social Studies**: Examine the effectiveness of different counterspeech strategies in mitigating hateful content online.
- **Prompt Engineering**: Investigate how prompts can guide LLMs to generate more empathetic or persuasive responses.

---

## ❗️ License
**PANDA** is released under the **MIT** license.  You are free to use the data in the project in research and commercial domains as long as follow the stipulations within the LICENCE file.

---



## 📜 Citations
If you use or reference **PANDA** in your research, kindly cite our pre-print:
```bibtex
@misc{bennie2025pandapairedantihate,
      title={PANDA -- Paired Anti-hate Narratives Dataset from Asia: Using an LLM-as-a-Judge to Create the First Chinese Counterspeech Dataset}, 
      author={Michael Bennie and Demi Zhang and Bushi Xiao and Jing Cao and Chryseis Xinyi Liu and Jian Meng and Alayo Tripp},
      year={2025},
      eprint={2501.00697},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2501.00697}, 
}
```
