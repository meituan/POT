# POT

This repository contains the data of the SIGIR 2022 Paper [Personalized Abstractive Opinion Tagging](https://github.com/MengxueZhao/POT).

If you have any question, please open an issue or contact <keninazhao@163.com>.

## PATag Dataset 

PATag is a large-scale Chinese restaurant reviews, opinion tags and user behavior dataset for personalized abstractive opinion tagging, which contains 555,297 reviews, 135,586 opinion tags and 15 million behavior actions from 68,732 users and 58,643 products(POIs). Each opinion tag is manually annotated to 28 predefined aspect categories, such as service, environment, taste and so on.

Intuitively, PATag mainly contains the following fields:
- review_id: Anonymized review id.
- user_id: Anonymized user id.
- poi_id: Anonymized product(poi) id.
- review_context: Historical reviews of user and product(poi). 
- opinion_tags: Ranked aspect-opinion tag pairs.
- is_click: Whether user has clicked product(poi).
- is_order: Whether user has ordered product(poi).
- is_favor: Whether user has favored product(poi).



### Review
```console
- UGC_Aspect_Word.npy 
- UGC_RankedAspects.npy
- UGC_RankedTags.npy
```

### User-Product(POI) pair
```console
- POI_User.npy 
- UGC_UP.npy
- User_POI_rank.npy 
- User_PR.npy
```

### Behavior
```console
- Click_UP.npy
- Buy_UP.npy
- Favor_UP.npy
```




We provide a runnable version of the PATag data. You can run this program directly using `data.pkl` and `matrix.pkl` in [Google Drive](https://drive.google.com/drive/folders/1ST6maKXhkab6bEuPdJtgRbPg2IjXaiDz?usp=sharing). You should download and move it under`./DataSet/`. 


You can view the details of the relevant data through `./DataSet/data_info.txt`, and `./DataSet/sample_for_data_pair.txt` is an instance of data pair.

If you want to get raw data and more processing details, please use this [Google form](https://docs.google.com/forms/d/e/1FAIpQLSc-SkZnd2rJqjSkPYOvi5ShvCHlbnYA8viS6459yEy27dPdYQ/viewform?usp=sf_link) to submit your information and request access to PATag.

## Prerequisites
```console
- CUDA >= 10.0
- Python >= 3.6
- PyTorch >= 1.7
```

## Setup
Check the packages needed or simply run the command:
```console
pip install -r requirements.txt
```

## Experiments
You can run the program with the following command: 
```bash
bash script/run.sh model_name gpus is_train
```

'model_name' can be 'POT', 'POT_woBehavior' or 'POT_woHGAT', to correspond to our proposed model, as well as two variants.

We support and recommend using multiple GPUs for training and a single GPU for testing.

### Train
```bash
bash script/run.sh POT 0,1,2,3 1
```

### Test
For reproducibility purposes, we place the model checkpoints at [Google Drive](https://drive.google.com/drive/folders/1ggxkJCFDW30gyZG4tXv5ecU0CNPr-0ko?usp=sharing). You should download and move it under `./Output/model_name/`, then you can run the trained models to test by using `best.pkl` and `best_memory.p`.

```bash
bash script/run.sh POT 0 0
```

## Reference
If you find our code useful, please cite our paper as follows:
```bibtex
@inproceedings{pot-2022,
  title={Personalized Abstractive Opinion Tagging},
  author={Mengxue, Zhao and Yang, Yang and Miao, Li and Jingang, Wang and Wei, Wu and Pengjie, Ren and de Rijke, Maarten and Zhaochun, Ren},
  booktitle={SIGIR},
  year={2022},
}
```
