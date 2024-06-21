Discussion about LLM efficiency:

Although LLM is relatively inefficient for generating samples, its overall time consumption is not particularly large because we select some samples for generation instead of using overall samples.
In addition, LLM has the following advantages: 

1) Automated generation capabilities. LLM itself has the ability to generate samples from linguistic descriptions and does not need to train a sample generator.

2) Flexibility for multi-task adaptation. LLM can be quickly tuned by In-Context Learning and a small number of parameters without the need to train a specialised scene generation model, which can improve the universality.

3) LLM can provide an explanation of the scene, which provides some interpretability compared to other black-box neural network generation methods.

   
	The low efficiency of LLM sample generation can be mitigated by some approaches.

1) By designing prompts that allow LLM to generate multiple samples at once based on a single sample, the efficiency of sample generation can be significantly improved and the size of the generated samples can be expanded [C. Chang, S. Wang, J. Zhang, J. Ge, and L. Li, “LLMScenario: Large Language Model Driven Scenario Generation,” IEEE Transactions on Systems, Man, and Cybernetics: Systems, doi: 10.1109/TSMC.2024.3392930.].

2) By describing multiple MetaData in the MetaData Prompt at the same time, and allowing LLM to generate based on multiple samples, the processing speed can also be significantly improved. In our experiments, we found that although this processing method has some impact on the quality of sample generation, especially more likely to generate duplicate samples, the overall efficiency is still significantly higher than single generation.
