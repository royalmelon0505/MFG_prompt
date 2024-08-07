# Mixing Left and Right-Hand Driving Data in a Hierarchical Framework with LLM Generation

Jiazhe Guo, Cheng Chang, Zhiheng Li, Li Li*

Here is the Prompt about the Sample Generation with LMM in this paper

![image](/fig/Prompt_Framework.png)


The `pre_prompt.md` reveals how to describe the tasks involved before actually input MetaData so that LLM can understand the requirements for generating new MetaData. The generation requirement is `The ego car moves slightly faster than before.`

The `gen_sample.md` gives a demo of the inputs and outputs of the actual generation of a sample.  Besides, the distribution of the generated samples in the future position for the overall dataset and the special dataset is visualized respectively.


How to write prompts for different scenario generation tasks is discussed in `modify_principle.md`

`pre_prompt2.md` and `pre_prompt3.md` are other Pre-prompts. 

The generation requirement of `pre_prompt2.md` is **I hope the other surrounding cars can move faster, and make the ego car move slower.** 

The generation requirement of `pre_prompt3.md` is **I hope the ego vehicle can change lane to the left.**

`LLM_efficiency.md` is the discussion about the efficiency of LLM generation
