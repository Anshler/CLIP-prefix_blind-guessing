# CLIP-Prefix for Image Captioning and an Experiment on Blind Image Guessing 👁️

Image caption generation resides at the intersection of computer vision and natural language processing, with its primary goal being the creation of descriptive and coherent textual narratives that faithfully depict the content of an image. 

We presents two models that leverage CLIP as the image encoder and fine-tune GPT-2 for caption generation on the Flickr30k and Flickr8k datasets. The first model utilizes a straightforward mapping network and outperforms the original architecture with a BLEU-1 score of ```0.700```, BLEU-4 score of ```0.257```, and ROUGE score of ```0.569``` on the Flickr8k dataset. The second model constitutes a new architecture exploring the boundaries of minimal visual information required for captioning. It incorporates CLIP's text encoder to produce input for the generator, while the image embedding serves solely as a validation mechanism. Despite its relatively lower performance, with a BLEU-1 score of ```0.546```, BLEU-4 score of ```0.108```, and ROUGE score of ```0.444``` on the Flickr8k dataset, this model demonstrates the decoder's ability to create captions based on keyword descriptions alone, without direct access to the context vector.

## Dataset

We use the [Flickr8k](https://www.kaggle.com/datasets/adityajn105/flickr8k) and [flickr30k](https://www.kaggle.com/datasets/eeshawn/flickr30k) dataset

## Evaluation

We use 6 metrics: Bleu-1 to 4, Meteor and Rouge

<!-- GitHub Markdown with LaTeX table -->
*Table 1: Result comparison of models trained on Flickr8k*
<table>
  <thead>
    <tr>
      <th style="text-align:center;">Models</th>
      <th style="text-align:center;">BLEU-1</th>
      <th style="text-align:center;">BLEU-2</th>
      <th style="text-align:center;">BLEU-3</th>
      <th style="text-align:center;">BLEU-4</th>
      <th style="text-align:center;">METEOR</th>
      <th style="text-align:center;">ROUGE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left;"><a href="https://github.com/rmokady/CLIP_prefix_caption">CLIP-prefix</a> (Original)</td>
      <td style="text-align:center;">0.698</td>
      <td style="text-align:center;">0.508</td>
      <td style="text-align:center;">0.363</td>
      <td style="text-align:center;">0.259</td>
      <td style="text-align:center;">0.257</td>
      <td style="text-align:center;">0.565</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: CLIP-prefix -- Gradient clipping</td>
      <td style="text-align:center;"><strong>0.700</strong></td>
      <td style="text-align:center;"><strong>0.513</strong></td>
      <td style="text-align:center;"><strong>0.372</strong></td>
      <td style="text-align:center;"><strong>0.262</strong></td>
      <td style="text-align:center;"><strong>0.257</strong></td>
      <td style="text-align:center;"><strong>0.569</strong></td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: CLIP-prefix -- Custom tokenizer</td>
      <td style="text-align:center;">0.682</td>
      <td style="text-align:center;">0.497</td>
      <td style="text-align:center;">0.351</td>
      <td style="text-align:center;">0.246</td>
      <td style="text-align:center;">0.249</td>
      <td style="text-align:center;">0.557</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: SBG -- One caption</td>
      <td style="text-align:center;">0.499</td>
      <td style="text-align:center;">0.276</td>
      <td style="text-align:center;">0.153</td>
      <td style="text-align:center;">0.087</td>
      <td style="text-align:center;">0.167</td>
      <td style="text-align:center;">0.410</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: SBG -- Top-2 caption</td>
      <td style="text-align:center;">0.520</td>
      <td style="text-align:center;">0.293</td>
      <td style="text-align:center;">0.161</td>
      <td style="text-align:center;">0.089</td>
      <td style="text-align:center;">0.179</td>
      <td style="text-align:center;">0.420</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: SBG -- Top-5 caption</td>
      <td style="text-align:center;"><strong>0.546</strong></td>
      <td style="text-align:center;"><strong>0.319</strong></td>
      <td style="text-align:center;"><strong>0.186</strong></td>
      <td style="text-align:center;"><strong>0.108</strong></td>
      <td style="text-align:center;"><strong>0.192</strong></td>
      <td style="text-align:center;"><strong>0.444</strong></td>
    </tr>
    <tr>
      <td style="text-align:left;"><a href="https://github.com/mtanti/rnn-role">Merge-RNN</a></td>
      <td style="text-align:center;">0.601</td>
      <td style="text-align:center;">0.411</td>
      <td style="text-align:center;">0.272</td>
      <td style="text-align:center;">0.179</td>
      <td style="text-align:center;">0.191</td>
      <td style="text-align:center;">0.439</td>
    </tr>
  </tbody>
</table>

<!-- GitHub Markdown with converted LaTeX table -->
*Table 2: Result comparison of models trained on Flickr30k*
<table>
  <thead>
    <tr>
      <th style="text-align:center;">Models</th>
      <th style="text-align:center;">BLEU-1</th>
      <th style="text-align:center;">BLEU-2</th>
      <th style="text-align:center;">BLEU-3</th>
      <th style="text-align:center;">BLEU-4</th>
      <th style="text-align:center;">METEOR</th>
      <th style="text-align:center;">ROUGE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left;">CLIP-prefix (Original)</td>
      <td style="text-align:center;">0.715</td>
      <td style="text-align:center;">0.506</td>
      <td style="text-align:center;">0.351</td>
      <td style="text-align:center;">0.243</td>
      <td style="text-align:center;">0.232</td>
      <td style="text-align:center;">0.529</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: CLIP-prefix -- Gradient clipping</td>
      <td style="text-align:center;">0.715</td>
      <td style="text-align:center;">0.503</td>
      <td style="text-align:center;">0.349</td>
      <td style="text-align:center;">0.235</td>
      <td style="text-align:center;"><strong>0.233</strong></td>
      <td style="text-align:center;">0.528</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: CLIP-prefix -- Custom tokenizer</td>
      <td style="text-align:center;"><strong>0.733</strong></td>
      <td style="text-align:center;"><strong>0.525</strong></td>
      <td style="text-align:center;"><strong>0.366</strong></td>
      <td style="text-align:center;"><strong>0.254</strong></td>
      <td style="text-align:center;">0.232</td>
      <td style="text-align:center;"><strong>0.536</strong></td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: SBG -- One caption</td>
      <td style="text-align:center;">0.495</td>
      <td style="text-align:center;">0.261</td>
      <td style="text-align:center;">0.139</td>
      <td style="text-align:center;">0.076</td>
      <td style="text-align:center;">0.154</td>
      <td style="text-align:center;">0.378</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: SBG -- Top-2 caption</td>
      <td style="text-align:center;">0.510</td>
      <td style="text-align:center;">0.279</td>
      <td style="text-align:center;">0.150</td>
      <td style="text-align:center;">0.082</td>
      <td style="text-align:center;">0.164</td>
      <td style="text-align:center;">0.391</td>
    </tr>
    <tr>
      <td style="text-align:left;">Ours: SBG -- Top-5 caption</td>
      <td style="text-align:center;"><strong>0.543</strong></td>
      <td style="text-align:center;"><strong>0.304</strong></td>
      <td style="text-align:center;"><strong>0.170</strong></td>
      <td style="text-align:center;"><strong>0.095</strong></td>
      <td style="text-align:center;"><strong>0.175</strong></td>
      <td style="text-align:center;"><strong>0.411</strong></td>
    </tr>
    <tr>
      <td style="text-align:left;">Merge-RNN</td>
      <td style="text-align:center;">0.596</td>
      <td style="text-align:center;">0.404</td>
      <td style="text-align:center;">0.270</td>
      <td style="text-align:center;">0.181</td>
      <td style="text-align:center;">0.175</td>
      <td style="text-align:center;">0.416</td>
    </tr>
  </tbody>
</table>

## Inference

Run the provided code on Colab. The model weights can be downloaded via Mediafire:
* [CLIP-prefix](https://www.mediafire.com/file/qof8qa7odm4dfck/flickr8k_prefix-030.pt/file) _(gradient clipping flickr8k)_
* [SBG](https://www.mediafire.com/file/9rjol6786rlmefx/model.safetensors/file) _(flickr8k)_

We also create a _Stable diffusion ([A1111 Webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui)) extension_ to interact with our models locally. Load from this [repo](https://github.com/Anshler/ICG_sd_extension)
