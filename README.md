# POT

This repository contains the data of the SIGIR 2022 Paper [Personalized Abstractive Opinion Tagging](https://github.com/MengxueZhao/POT).

If you have any question, please open an issue or contact <keninazhao@163.com>.

## PATag Dataset 

PATag is a large-scale Chinese restaurant reviews, opinion tags and user behavior dataset for personalized abstractive opinion tagging, which contains 555,297 reviews, 135,586 opinion tags and 15 million behavior actions from 68,732 users and 58,643 products(POIs). Each opinion tag is manually annotated to 28 predefined aspect categories, such as service, environment, taste and so on.

Intuitively, PATag mainly contains the following fields and `sample_for_data_field.txt` is an instance of PATag.
- review_id: Anonymized review id.
- user_id: Anonymized user id.
- poi_id: Anonymized product(POI) id.
- review_context: Historical reviews of user and product(POI). 
- opinion_tags: Ranked aspect-opinion tag pairs.
- is_click: Whether user has clicked product(POI).
- is_order: Whether user has ordered product(POI).
- is_favor: Whether user has favored product(POI).


For ease of analysis and processing, we organize the data into multiple npy files. You can download them by [Google Drive](https://drive.google.com/drive/folders/1ST6maKXhkab6bEuPdJtgRbPg2IjXaiDz?usp=sharing) and process them with `data_reader.py` and `data_loader.py`, then you have the data that [POT](https://github.com/MengxueZhao/POT) needed.


### Review
For each user, we divide his reviews into historical reviews and recent reviews. There are 419,711 historical reviews and 135,586 recent reviews in PATag. We only use meaningful sentences in reviews as input, i.e. review sentences that can correspond to predefined aspects. As multiple review sentences may link to the same aspect in reviews, we only select the one with the highest confidence as the opinion tag. Briefly, we use meaningful sentences from historical reviews as input, and output the meaningful sentences with the highest confidence for a single aspect in recent reviews, i.e., opinion tag.

- UGC_Aspect_Word.npy: 
- UGC_RankedAspects.npy: 
- UGC_RankedTags.npy: 


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
