# DialoGPT Small
Based on the paper: Towards Emotional Support Dialog Systems (https://arxiv.org/abs/2106.01144)

codes_zcj is the version reproduced by @chujiezheng. This version was used for this experiment due to its ease of reproducibility.                

**0. Preparing Enviroment**

conda env create -f env.yml -n cuda
conda activate cuda
Downloading Model
You should **first download the DialoGPT-small model** and replace the fake pytorch_model.bin file in DialoGPT with the true one.

If you would like to evaluate generated results with Embedding-based similarity, you can download my prepared embedding files from HuggingFace.

**About Postfix**

_vanilla denotes the variant directly fine-tuned on ESConv without using strategies
_strat denotes the one that additionally uses the strategy information and supervision

**1. Preprocessing Training Data**
First, enter _reformat and run python process.py.

Then, run bash RUN/prepare_vanilla_dialogpt.sh to preprocess the training data.

**2. Training Your Model**

Run bash RUN/train_vanilla_dialogpt.sh to train your model.

**3. Inference with Your Model**

Every time of model training will create a new folder in DATA/{inputter_name}.{config_name}, which is named after the time when the training starts. You should select a checkpoint (it may be based on the PPL of validation), and replace the checkpoint path in RUN/infer_vanilla_dialogpt.sh --load_checkpoint with the path of your selected checkpoint.

Then, run bash RUN/infer_vanilla_dialogpt.sh to do the inference.

Note: When you run infer_strat.sh, you can change GOLDEN_TRUTH in inputters/PARAMS.py to control whether use the golden strategy during inference.

**4. Interacting with Your Model**

Similar to inference, after designating the checkpoint in RUN/interact_vanilla_dialogpt.sh --load_checkpoint, run bash RUN/interact_vanilla.sh.

**Note 1: Reproduction Purposes**
For reproduction purposes, you need to:
1. Download the files from: https://drive.google.com/drive/folders/1-HhUpWSkLnxiGHMPkqXTjhB7Ak81iTXV?usp=drive_link
2. Upload them to the Google Drive content environment.
3. Follow the steps described in the previous section.

**Note 2: Update function and libraries**
Follow the steps from BlenderBot to download GloVe.
