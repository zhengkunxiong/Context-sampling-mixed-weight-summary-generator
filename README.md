# cmsg


## Dependency

Install dependencies via:
```
conda create -n cmsg python=3.9.6
conda activate cmsg
conda install pytorch==1.8.0 torchvision==0.9.0 torchaudio==0.8.0 cudatoolkit=11.1 -c pytorch -c conda-forge
pip install nltk==3.6.2 pyrouge==0.1.3 transformers==4.8.1 rouge==1.0.0 datasets==1.11.0
```

## Folder Structure
- dataloaders: the python scripts to convert original dataset to the uniform format.
- oracle: Scripts to generate extractive oracles
- utils: Various utility functions, such as cleaning and rouge
- Experiment.py: Main file for our model
- config.py: Set model configuration
- Modules: Contains implementation of our dynamic extraction module
- test.py: Run test set
- train.py: Train the model

## Training and Evaluation

### Download the Datasets and Models
- Download QMSum dataset from https://github.com/Yale-LILY/QMSum
- Download GovReport dataset from https://github.com/luyang-huang96/LongDocSum/tree/main/Model
- Download ArXiv from Hugging Face at https://huggingface.co/datasets/scientific_papers
- We provide cleaned dataset with oracle (in jsonl) for QMSum and GovReport from [Google Drive](https://drive.google.com/drive/folders/1xWP65_D3jmo2147xAYlfHJGAzXpFSdxR?usp=sharing). Download them and place them under `data/`
- ArXiv dataset and oracles are loaded separately

### Training the Model
- After we clean the datasets and process the oracles, setup the paths of scripts at `dataloaders/*.py`
- Set the `self.target_task` flag in `config.py` to choose the target task
- Train the model by the command: 

```
python train.py
```

### Evaluation
- First download the checkpoint from [Google Drive](https://drive.google.com/drive/folders/1xSYhOB-z9dwKz684yaer3wdXj4ajQnsv?usp=sharing) and place the folders under `./outputs/saved_model/`
- Set the `self.target_task` flag in `config.py` to choose the target task
```
python test.py
```

## Citation
```bibtex
@inproceedings{mao2021dyle,
  title={DYLE: Dynamic Latent Extraction for Abstractive Long-Input Summarization},
  author={Mao, Ziming and Wu, Chen Henry and Ni, Ansong and Zhang, Yusen and Zhang, Rui and Yu, Tao and Deb, Budhaditya and Zhu, Chenguang and Awadallah, Ahmed H and Radev, Dragomir},
  booktitle={ACL 2022},
  year={2022}
}
``` 
