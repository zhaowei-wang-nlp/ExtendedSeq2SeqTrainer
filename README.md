# Extended transformers.Seq2SeqTrainer
This repo extend [the seq2seq Trainer](https://github.com/huggingface/transformers/blob/main/src/transformers/trainer_seq2seq.py) in [Huggingface Transformers](https://github.com/huggingface/transformers).
At first, this repo was based on Transformers [v4.17.0](https://github.com/huggingface/transformers/tree/v4.17.0), where the [Seq2SeqTrainer](https://github.com/huggingface/transformers/blob/v4.17.0/src/transformers/trainer_seq2seq.py)
only support two parameters in decoding: `max_length` and `num_beams`. `seq2seqtrainer.py` in this repo
modified code and supports all parameters of the function [generate](https://huggingface.co/docs/transformers/v4.24.0/en/main_classes/text_generation#transformers.generation_utils.GenerationMixin.generate)

Current (Nov 12, 2022) latest version of Transformers is v4.24.0, where the Seq2SeqTrainer support most parameters in the function generate. However, it still
doesn't support `num_return_sequences`, which is used to generate more than one
output sequences for an input sequence. This repo supports it.


# How to use?
`seq2seqtrainer.py` contains modified `Seq2SeqTrainer`, which is called `ExtendedSeq2SeqTrainer`.
In your own code, replace `Seq2SeqTrainer` with `ExtendedSeq2SeqTrainer`.
The function `ExtendedSeq2SeqTrainer.generate` is used to decode, equivalent to `Seq2SeqTrainer.predict`.

`fine-tune_example.py` provides an example of replacing `Seq2SeqTrainer` with `ExtendedSeq2SeqTrainer`,
modified from the example code `run_summarization.py` [link](https://github.com/huggingface/transformers/blob/main/examples/pytorch/summarization/run_summarization.py)


## Contributing
If you find any typo or bug, please open an issue.