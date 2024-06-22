Discussion about LLM efficiency:

we use gpt-3.5-turbo-1106 and using the OpenAI API interface to test the efficiency of sample generation. We randomly input 198 samples, and the generation time of LLM for each sample is：

![image](/fig/gen_time.png)

Under normal circumstances, the efficiency of LLM's sample generation is about 5-15s per sample, excluding the anomaly which cost extra long time, the average generation time is 9.75s. 

Of these 198 input samples, LLM generate 166 samples ( 83.8% ) as requested. It means that the generated samples correctly contained the state, trajectory, and start point, and there were no problems such as missing a bracket. Of these 166 samples, 139 are reasonable. The determination of whether a generated sample is reasonable is based on the four post-processing rules in the manuscript. Given that it can be generated as requested, the probability that a generated sample is reasonable is about 83.7%. Overall, the probability that the LLM generates a reasonable sample is 70.2%. It is worth to notice that the probability to generate reasonable samples before the addition of the MLP is about 20%. 

Although LLM is relatively inefficient for generating samples, its overall time consumption is not particularly large because we select some samples for generation instead of using overall samples.
In addition, LLM has the following advantages: 

- Automated generation capabilities. LLM itself has the ability to generate samples from linguistic descriptions and does not need to train a sample generator.

- Flexibility for multi-task adaptation. LLM can be quickly tuned by In-Context Learning and a small number of parameters without the need to train a specialised scene generation model, which can improve the universality.

- LLM can provide an explanation of the scene, which provides some interpretability compared to other black-box neural network generation methods.

   
The low efficiency of LLM sample generation can be mitigated by some approaches.

- By designing prompts that allow LLM to generate multiple samples at once based on a single sample, the efficiency of sample generation can be significantly improved and the size of the generated samples can be expanded [C. Chang, S. Wang, J. Zhang, J. Ge, and L. Li, “LLMScenario: Large Language Model Driven Scenario Generation,” IEEE Transactions on Systems, Man, and Cybernetics: Systems, doi: 10.1109/TSMC.2024.3392930.].

- By describing multiple MetaData in the MetaData Prompt at the same time, and allowing LLM to generate based on multiple samples, the processing speed can also be significantly improved. In our experiments, we found that although this processing method has some impact on the quality of sample generation, especially more likely to generate duplicate samples, the overall efficiency is still significantly higher than single generation.
