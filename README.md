# CLIP-Prefix for Image Captioning and an Experiment on Blind Image Guessing 👁️

Image caption generation resides at the intersection of computer vision and natural language processing, with its primary goal being the creation of descriptive and coherent textual narratives that faithfully depict the content of an image. 

We presents two models that leverage CLIP as the image encoder and fine-tune GPT-2 for caption generation on the Flickr30k and Flickr8k datasets. The first model utilizes a straightforward mapping network and outperforms the original architecture with a BLEU-1 score of ```0.700```, BLEU-4 score of ```0.257```, and ROUGE score of ```0.569``` on the Flickr8k dataset. The second model constitutes a new architecture exploring the boundaries of minimal visual information required for captioning. It incorporates CLIP's text encoder to produce input for the generator, while the image embedding serves solely as a validation mechanism. Despite its relatively lower performance, with a BLEU-1 score of ```0.546```, BLEU-4 score of ```0.108```, and ROUGE score of ```0.444``` on the Flickr8k dataset, this model demonstrates the decoder's ability to create captions based on keyword descriptions alone, without direct access to the context vector.

## Dataset

We use the [Flickr8k](https://www.kaggle.com/datasets/adityajn105/flickr8k) and [flickr30k](https://www.kaggle.com/datasets/eeshawn/flickr30k) dataset


