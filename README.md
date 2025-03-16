# Mixing Left and Right-Hand Driving Data in a Hierarchical Framework with LLM Generation

### [Paper](https://ieeexplore.ieee.org/document/10636276) 
IEEE Robotics and Automation Letters (RAL) 2024

Jiazhe Guo, Cheng Chang, Zhiheng Li, Li Li*

### Abstract 
Data-driven trajectory prediction is critical in autonomous vehicles, which requires high-quality data. However, discussions about the compatibility of data collected from different countries remain limited, with a typical issue being the different driving rules in various countries. Therefore, we propose a hierarchical framework for mixing left and right-hand driving data to support trajectory prediction. Integrated with a proposed LLM-based sample generation method, the framework utilizes mirroring, MMD and sample generation incrementally to reduce the domain gap between datasets. By testing the mixed results on two typical trajectory datasets, we demonstrate that this method enhances the performance of models trained on left-hand driving data when applied to right-hand driving scenarios.

### LLM Prompt
Here is the Prompt about the Sample Generation with LLM in this paper

![image](/fig/Prompt_Framework.png)


The `pre_prompt.md` reveals how to describe the tasks involved before actually input MetaData so that LLM can understand the requirements for generating new MetaData. The generation requirement is `The ego car moves slightly faster than before.`

The `gen_sample.md` gives a demo of the inputs and outputs of the actual generation of a sample.  Besides, the distribution of the generated samples in the future position for the overall dataset and the special dataset is visualized respectively.


How to write prompts for different scenario generation tasks is discussed in `modify_principle.md`

`pre_prompt2.md` and `pre_prompt3.md` are other Pre-prompts. 

The generation requirement of `pre_prompt2.md` is **I hope the other surrounding cars can move faster, and make the ego car move slower.** 

The generation requirement of `pre_prompt3.md` is **I hope the ego vehicle can change lane to the left.**

`LLM_efficiency.md` is the discussion about the efficiency of LLM generation
