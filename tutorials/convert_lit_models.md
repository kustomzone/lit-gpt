## Converting a Lit-GPT Formatted Model to its Original Format

Several models retrieved from external sources must be reformatted with naming conventions for Lit-GPT weights before finetuning. We've provided a helpful script to convert models finetuned with Lit-GPT back to their original format.

The way the script is used depends on the finetuning method. The commands for converting a model back to its original format after using one of the several finetuning methods supported by Lit-GPT are shown below.

> [!NOTE]\
> all examples use the Meta Llama-2-7b-chat-hf checkpoints and Alpaca dataset during finetuning

> [!NOTE]\
> finetuned checkpoints will be saved to a subdirectory in a main directory named `out` e.g. finetuning with adapter_v2 will save checkpoints in `out/adapter_v2/alpaca`. that new subdirectory is used in the `--checkpoint_dir` in convert_lit_checkpoint

### Full Finetuning

After full finetuning, your checkpoint directory will contain a file named `lit_model_finetuned.pth`and converting the finetuned model back to its original weights naming convention can be done by setting the `--checkpoint_name` with:

```sh
python scripts/convert_lit_checkpoint.py \
    --checkpoint_name lit_model_finetuned.pth  \
    --checkpoint_dir out/adapter/alpaca/ \
    --model_name Llama-2-7b-chat-hf
```

### Adapter and Adapter V2 Finetuning

After finetuning with either Adapter technique, your checkpoint directory will contain a file named `lit_model_adapter_finetuned.pth` and converting the finetuned model back to its original weights naming convention can be done by setting the `--checkpoint_name` with:

```sh
python scripts/convert_lit_checkpoint.py \
    --checkpoint_name lit_model_adapter_finetuned.pth  \
    --checkpoint_dir out/adapter/alpaca/ \
    --model_name Llama-2-7b-chat-hf
```

### LoRA Finetuning

After finetuning with LoRA, your checkpoint directory will contain a file named `lit_model_lora_finetuned.pth` and converting the finetuned model back to its original weights naming convention can be done by setting the `--checkpoint_name` with:

```sh
python scripts/convert_lit_checkpoint.py \
    --checkpoint_name lit_model_lora_finetuned.pth  \
    --checkpoint_dir out/adapter/alpaca/ \
    --model_name Llama-2-7b-chat-hf
```

### Submitting Issues

If you run into errors when using convert_lit_checkpoint, please [submit an issue](https://github.com/Lightning-AI/lit-gpt/issues) in GitHub.
