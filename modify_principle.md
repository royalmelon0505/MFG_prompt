1) For sample generation with the same priori knowledge, the `Description of new Scene` in  `Pre-prompt` and `MetaData Prompt` do not need to be modified,
   only the content in  `Ori MetaData` needs to be modified.

2) For sample generation with different priori knowledge, `Example` needs to be modified in `Pre-prompt` and `Description of new Scene` needs to be modified in `MetaData Prompt`.
   Since `Example` contains a complete input and output, its format is the same as that of MetaData Prompt, the `Output` section of Example needs to reflect the introduction of a priori knowledge.
   For example, if we want to generate a sample of a vehicle *turning right*, and the original MetaData is *go straight*, then in `Example`, the `Input` needs to be a *go straight* MetaData
   and the `Output` MetaData should be a sample of a vehicle *turning right*, which is shown in below to reveal the modifications according to different scenario.
   The red part in the figure indicates the modified prompt.

The prompt design for different scenarios is :
![Image text](/fig/mod_example_vis.png)

The generated samples is:
![Image text](/fig/Gen_diff_vis.png)

A,B,C is scene generated by GPT-3.5. The description of every scene is list below. A : "I hope the ego car can move faster"; B:"I hope the other surrounding cars can move faster, and make the ego car move slower.";C:"I hope the ego vehicle can change lane to the left"
