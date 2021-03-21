Capstone Report

 # Data Cleaning:
    - The Dataset is a text file with pair's of english text and python code.
    - Each example is seperated by a new_line character and '#' symbol**(\n#) **.
    - Additionally some sentences start with a space after the '#' symbol and some don't, to remove them the queue is first tokenised and          checked for space's in the beginning of the sentence.

# Data Preparation:
    * During the training of the model it was found that two similar queue's when passed through the model would give different result even though they mean the same.
        Ex:
        queue-1:"write a program to add two numbers"

        queue-2:"add two numbers"
     *As an attempt to overcome this problem the queue is modified to remove some common words like           "write","program","function","to",......Due to this the total examples have doubled and is working as an augmentation technique.This change although improved the result of some queue's not all of them were giving the expected result.
     * As an attempt to overcome this problem the queue is modified to remove some common words like "write","program","function","to",......Due to this the total examples have doubled and is working as an augmentation technique.This change although improved the result of some queue's not all of them were giving the expected result


# Model Architecture:
    * The detailed explanation of the model architecture is available in the link [here.](https://www.linkedin.com/pulse/transformers-siva-vamsi/?trackingId=I%2BRg%2B0s7Sw2BN7qgcastdg%3D%3D) 




# Python Code Embedding:
    *  Python code snippet's are first tokenised using the tokenize library. 
    * "INDENT" token is given special care and indent(4 space's) are replaced by "\t". 
    * Some snippet's contain irregular number of space's which are rounded off. 
    * Each snippet is tokenised and all the tokenised snippet's are appended to a list which is used to train the embedding's. 
    * Embedding's are trained using the gensim library Word2Vec for a total of 100 epoch's. 
    * All other parameter's of the Word2Vec model is kept default. 
    * The Dimension of the Word2Vec embedding's are same as the Dimension of the embedding layer present in the decoder part of the Transformer arhitecture. 
    * This is important so that the embedding vector's from Word2Vec can be transformed to the embedding of the decoder in transformer's architecture.

# Evaluation Metrics:
    * The Evaluation metric used is BLEU score which after training for 50 epochs is close to 60(+/- 2)


# ."25"  example output from your model

#.Attention graph/images between text and "python-code"


# Others:
    * While the model is predicting the code snippet's for which the query matches in the dataset, it is struggling to predict for querie's which are not exactly the same in the training dataset. 
    * It feels as if the output is being generated by referencing a dictionary where the queries match with the input queries.
    * The loss function used is a combination of two different loss function's scaled accordingly. While this is acting as a regularisation        technique it is not helping in the learning of the model.

#References:
