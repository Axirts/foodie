# Foodie

## Abstract
Cooking is an art and art takes creativity. Machines aren't "creative" in the same sense as we are, but they certainly have the ability to mimic human creativity. Or are they? [Some](https://www.thetrumpet.com/8960-the-mystery-of-human-creativity-explained) claim that creativity is unique to humans. California State University, [Northridge cites Robert E. Franken](http://www.csun.edu/~vcpsy00h/creativity/define.htm) in defining creativity "as the tendency to generate or recognize ideas, alternatives, or possibilities that may be useful in solving problems, communicating with others, and entertaining ourselves and others." Based on this definition, machines can be just as creative as humans and more efficiently at it as well as they can analyze much more information than we can. There are multiple purposes of this project:

- Gather, clean, and understand recipe data
- Take a statistical approach to describe the data
- Make a model that can parse enough information from said data to understand the science behind cooking
- Make a model that emulates human creativity by attempting to create new recipes
    - This can be in the form of applying deep learning to modify existing recipes or create them from scratch based on an understanding of how cooking works
- Demonstrate machines as creative entities

## Business Application
As a research project, the goal I set forth with was to test combinations of data analysis and modeling techniques to achieve results a human can appreciate. The business implication of successfully creating such a model are only limited by the entrepreneurial skills of whoever uses it. For example, the model could be used to:
   - propose new restaurant menus for "fusion" cuisine
   - adapt existing recipes to specific diets
   - 
Furthermore, the models are interpreting plain (English) language instructions and as such, could be applied to more than just recipes. 

## File Structure

```
root
│   README.md
│   exec_summary.md    
│
└───code
│   │   1_collection.ipynb
│   │   2_cleaning.ipynb
│   │   3_eda.ipynb
│   │   4.1_kmeans.ipynb
│   │   4.2_word2vec.ipynb
│   │   4.3_markov.ipynb
│
└───data
│   │   recipes.csv
│   │
│   └───api_data
│       │   001.json
│       │   002.json
│       │   003.json
│       │   ...
│
└───visualizations
    │   vis1
    │
```

## Resources
- Data:
    - spoonacular api via [rapidapi](https://rapidapi.com/spoonacular/api/recipe-food-nutrition/)
    - Further information on fodmap [here](https://www.hopkinsmedicine.org/health/wellness-and-prevention/fodmap-diet-what-you-need-to-know)
    - spaCy nlp preprocessor [documentation](https://spacy.io/usage/models) used to clean the data
    - spaCy pipeline [example](https://spacy.io/usage/processing-pipelines)
    
- Word2Vec:
    - Gensim Word2Vec library [documentation](https://radimrehurek.com/gensim/models/word2vec.html)
    - blog [post](https://jalammar.github.io/illustrated-word2vec/) detailing how Word2Vec works
    - blog [post](https://towardsdatascience.com/creating-word-embeddings-coding-the-word2vec-algorithm-in-python-using-deep-learning-b337d0ba17a8) describing manual creation of Word2Vec using keras neural network layers 
    - blog [post](https://towardsdatascience.com/text-classification-with-nlp-tf-idf-vs-word2vec-vs-bert-41ff868d1794) comparing Tf-Idf, word2vec, and BERT 
    
- Markov Chains:
    - markovify library [repo](https://github.com/jsvine/markovify)
    - blog [post](https://towardsdatascience.com/simulating-text-with-markov-chains-in-python-1a27e6d13fc6) with markovify example
    - blog [post](https://towardsdatascience.com/text-generation-with-markov-chains-an-introduction-to-using-markovify-742e6680dc33) with markovify example
    - [video](https://www.youtube.com/watch?v=ibFeUX5F_fw) detailing how markov chains work
