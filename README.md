## Encoder-Decoder

**Encoder-Decoder architecture** is a traditional concept of converting a signal using an Encoder which is then translated back into required form using a Decoder.

![Transformer_1](/assets/Graph.png)

## Encoder-Decoder in NLP tasks

The same concept of Encoder-Decoder architecture isnspires state of the art Sequence to Sequence learning task like Language translation, Text summarization tasks which harness the power of State-of-Art Transformers like **BERT, Roberta, GPT2 etc.** where the Encoder is essentially a transformer model which encodes the information in the text in a **mathematical-tensor** employing **Self-Attention** heads which uses Key,Value and Query which solves the problem of traditional RNN's & LSTM's of short window of attention and vanishing gradients.

![Transformer_1](/assets/Encoder-Decoder.png)

This **mathematical-tensor** from Encoder is connected with the Decoder layers using a **Cross-Attention** layer (which helps in encoding the previously generated output ex. in machine translation every next token is chosen using the previous tokens genereated and the Encoder tensor)
This Cross-Attention layer helps the Decoder tensors mapped to the Encoder tensors and generate an intermediate embedding states which help generate the output.

## ViT (Vision Transformer)

Recently a paper on Vision Transformers "**An Image is worth 16x16 words**" which flashes an idea that every Image can be interpreted as chunk of images as tokens similiar to words in a sentence and this **3d Image tensor tokens** can be used as an input to the transformer for any CV tasks. This solves the challenge of CNN of limited association as the basic idea of CNN's are tying only regional pixels using a kernel which convolutes all over the image.

![Transformer_1](/assets/vit_figure.png)

## Vision Encoder Decoder
Thus using the above 2 ideas the Task of Image captioning can be tackled as Encoder & Decoder Task where the 
1) Task 1 - **Input to the decoder is an Image**, which can be tackeld by a Vision Transformer (ViT).
2) Task 2 - **Output from the Decoder is Text describing the objects in the image**, which can be tackled by Roberta, BERT or any other state of the art Language model

![Transformer_1](/assets/Image_captioning.png)

As we can see from above, The ViT transformer encodes the Information from the Images & the Decoder using cross attention generates the captions on the data.

# Training
#### All the training captions and Image file names are stored in [data.json](/data.json). You can download the images from [here]( https://www.kaggle.com/datasets/adityajn105/flickr8k)

### Step 1 - Train Decoder Model on the corpus of captions 
(You can build your own Tokenizer from scratch as done in the [IPYNB](https://gist.github.com/kalpesh22-21/12d58a86114f23d1492b57dc06cf91e3) above) 

### Step 2 - Train Vision Encoder Decoder model
(Refer [IPYNB] (https://gist.github.com/kalpesh22-21/cb93603d00c7d36df3b0c8bdc67f0aae))

# Results
After training the model only 20% of data for 2 iteration (due to compute unavailability) we can see we get a precision of 15% and recall of 15.5% on test data from below.

![Training_Iterations](/assets/Iter.png)


The model also generates fairly accurate captions as shown below.

![caption_1](/assets/6.png)

## More examples:

![caption_1](/assets/1.png)
![caption_1](/assets/2.png)
![caption_1](/assets/3.png)
![caption_1](/assets/4.png)


# References:
https://github.com/google-research/vision_transformer

https://huggingface.co/docs/transformers/model_doc/encoder-decoder
