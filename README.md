# NLP from Scratch (No Pretrained Models)

**_Approach:_**

• Download the dataset

• Use a tokenizer to convert the input sequence of words into integers.

• Create a model that embeds the semantic meaning of each individual word into a vector.

• Give the vectors positional embedding so that the semantic meaning of their positions are not lost.

• Using a simple pytorch nn.TransformerEncoderLayer and nn.TransformerEncoder get the contextual meaning of the input sequence.

• Using the contextual meaning of the previous sequence predict the next token in the sequence using a fully connected layer.

• Compare the predicted token to the target token and use CrossEntropyLoss for backpropagation.

**Details:_**

• For the tokenizer used hugging face's tokenizer library, and made a custom tokenizer for the dataset used here, because its not a general purpose tokenizer, the speed of encoding is much faster. The tokenizer the resulted for the dataset was a subword tokenizer, which leads to much greater inference. 

• The dataset used is WikiText103, which is a dataset containing 103 million groups of sentences, each data point in the code is the single sentence in the dataset which is then padded to a specified length 

• Because the dataset is too huge to load all at once, for the formation of proper embedding a small chunk of data is loaded and the model is trained on that. Once the training is done the next chunk of data is loaded, and so on. 

• The model achieves english like sentences, however the complete coherence of sentences are still missing, perhaps more training is required or a bigger model is needed(unfortunately I do not have the resources to train a bigger model without spending hours).
