# Multi-Fractal Head Attention
This is my first branching-off from my new [base model]() repo meant mainly as a test since i don't expect this idea to perform that well. In it i'll be saying fuck it to efficiency and giving each attention block heads of a variety of sizes

# File Structure
- `inference.ipynb`: open this notebook if you just want to load a model and perform inference
- `train.ipynb`: open this notebook to train a model
- `build_tokenizer.ipynb`: open this notebook to train a Character-Pair Encoding tokenizer (like Byte-Pair Encoding except I used the 95 unique characters that show up in the TinyStories dataset instead of actual bytes)
- `testing_modules.ipynb`: creates easy printouts that allow you to follow the progression of tensor shapes for demonstration & debugging purposes of all the modules in `model.py`. If you're building new modules for a novel architecture idea you have then this notebook will be of extreme value to you
- `model_evaluation.ipynb`: open this notebook to compare different models against each other. includes loss curve plots and topk teacher-forcing accuracy rate
- `hyperparameter_search.ipynb`: eventually in here i'd like to build an automated system that tests different hyperparameter configurations & skips past ones that go over the ram limit, but rn it's empty
- `config.py`: all of the editable model and training settings
- `inference.py`: functions for performing inference, used in `inference.ipynb`
- `train.py`: functions for training a model, used in `train.ipynb`
- `model.py`: the actual pytorch modules like RMSNorm, MLP, MQA, ResidualLayer, etc
- `tokenizer.py`: an overly-simplistic and annoyingly inefficient tokenizer with bos & eos tokens and post-sequence padding
- `tools.py`: A variety of functions & classes that don't fit elsewhere and/or are used by more than one of the jupyter notebooks. Of note is the `LoggingModule`, a wrapper for pytorch's `nn.module` that makes for very pretty & easy to follow printing of the progression of tensor shapes over in `testing_modules.ipynb`
- `model_code/`
    - `baseGPT.py`
    - `baseGPT_config.py`
    - `modules/`
        - `attentions.py`
        - `norms.py`
        - `feedforward.py`
- `tokenizers/`
    - `bpe_tokenizer_{95, 128, 256, 512, 1024, 2048}.model`: the 95 one is character-wise tokenization
- `trained_models/`
    - `0.5m_{short_and_thick, 5foot11_and_skinnyfat, tall_and_skinny}/`: a series of 0.5m parameter models designed to be compared against one another
        - `log_data.csv`: record of loss & perplexity data over the course of training
        - `model_config.json`: hyperparameters of the model
        - `model.pth`: weights of the model
        - `train_config.json`: hyperparameters of the training loop used to train the model
- `requirements.txt` - I should probably change this to only include the packages that are actually necessary and not be so strict on versions. The command I used to get this list is `pip freeze | grep -v " @ file://" > requirements.txt`, lmk if you know of a better method

# how to contribute
Other than the below TODO lists, appreciated contributions include bug fixes, adding more verbose comment explanations of what the code is doing, general readability edits, efficiency edits, taking better advantage of the `LoggingModule`, etc. Because I'm not super knowledgeable on how collaborating on git projects works and I tend to edit directly on the main branch, please reach out and communicate with me about any edits you plan to make so that I can avoid editing the same files. [Click here to join my discord server](https://discord.gg/hTYQyDPpr9)

# definite TODOs
- [ ] add mult-fractal head attention module to `model_code/modules/attentions.py`
- [ ] train model & compare

# check me out
- guides on how to build miniature versions of popular models from scratch: [minGemma](https://github.com/evintunador/minGemma), [minGrok](https://github.com/evintunador/minGrok), and [minLlama3](https://github.com/evintunador/minLlama3)
- [my YouTube channel](https://www.youtube.com/@Tunadorable)
- my [other links](https://linktr.ee/tunadorable)