## Instruction Tuning LLAMA3 
This repo uses the `torchtune` for instruction tuning the llama3 pretrained model on mathematical tasks using LORA. 

### Wandb report link
https://wandb.ai/som/torchtune_llama3?nw=nwusersom

## Instruction_tuned Model 
https://huggingface.co/Someshfengde/llama-3-instruction-tuned-AIMO

### Original metallama model 
https://huggingface.co/meta-llama/Meta-Llama-3-8B


## For running this project 
```
> pip install poetry 
> poetry install 
```
Further commands over shell terminal


### To download the model 
```
tune download meta-llama/Meta-Llama-3-8B \
--output-dir llama3-8b-hf \
--hf-token <HF_TOKEN> 
```

**To start instruction tuning with lora and torchtune**
```
tune run lora_finetune_single_device --config ./lora_finetune_single_device.yaml
```


### To quantize the model
```
tune run quantize --config ./quantization_config.yaml

```

### To generate inference from model.
```
tune run generate --config ./generation_config.yaml \
prompt="what is 2 + 2."
```

## Dataset used 
Contains various math problems (Math olympiad problems.)

https://huggingface.co/datasets/Someshfengde/AIMO_dataset

### Evaluations 

**To run evaluations** 
```
tune run eleuther_eval --config ./eval_config.yaml
```
### TruthfulQA: 0.42
![alt text](images/image.png)

### MMLU Abstract Algebra: 0.35
![alt text](images/image-1.png)

### MATHQA: 0.33
![alt text](images/image-2.png)

### Agieval_sat_math: 0.31 
![alt text](images/image-3.png)