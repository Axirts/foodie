## Executive summary:
There were multiple goals set for this project at its inception but all of these changed slightly as time progressed.
    - The primary goal is to create recipe steps by using natural language processing on a corpus of recipes.
    - The primary changes over time were the models used
---
### The data was acquired from the spoonacular API consisting of recipes and their:
    - description of the dish
    - ingredients
    - preparation instructions
    - nutritional information
---
### Challenges
- The primary risk associated with such a project is that of wasting ~~time~~ money and money. The nature of this project is research, and as such, profit made off of conclusions would come from further application, not the models themselves. 
- There were plenty of difficulties with the api that I came across when attempting to clean and model the data.
    - the api restricted searches to 100 / call and 500 total per day
    - the normal method of requesting a recipe results in needing multiple calls, one for the basic information and a separate one for instructions
    - using random recipe requests returns all information, but it takes it from "popular" recipes and ended up returning duplicates that needed to be cleaned out
    - it was apparent that even native English speakers were lazy and sloppy with their writing online
---
### Metrics
- The pupose of this experiment is to create and analyze an unsupervised model. As it is a natural language unsupervised model, the best metric for it is "does it make sense", or "is it interpretable to a normal human?"
- Further metrics could include:
    - is the recipe actually cookable
    - is it obvious 
---
### Summary of process and statistical analysis:
- Step 1: First, a python function was created to automate api calls to spoonacular. This worked by making 4 calls, each requesting 100 points of data, and saving the returned json as a file that incremented in the /data/api_data folder. 4 calls rather than 5 were made to leave calls available in case I wished to play with other api request settings. A 5th call was often manually made.
- Step 2: Once data was saved as a json, with-open and pandas was used to load the file as a dataframe. The dataframe still contained nested json formatting and functions were created to strip relevant information and reduce the size its size. After the dataframe contained desired information, it was saved as a csv file in /data.
- Step 3: Feature engineering in the form of count vectorizing was then applied to the cleaned csv. This allowed for basic EDA such that I knew what to expect when training models. Here is were I learned that 20% of popular recipes involved chicken, the most prominent of all ingredients. 
- Step 4: KMeans models were created on "simplifiedIngredients", "simplifiedInstructions", and "summary" in an attempt to fill in missing values of the "cuisine" and "dishType" features. The imputation is not currently complete as the model seemed to really only identify vegitarian recipes, a feature that did not have missing values.
- Step 5: Word2Vec was set up in preparation of applying a change in cuisine type from one region to another's. This has not been used as the text generating model itself needs more progress.
- Step 6: The text generation was originally designed around using a BERT model with a seed sentence starter to complete instructions. BERT is designed to complete missing words in sentences and as such, a single word was predicted and the entire output was then repeatedly fed back into the model to finish a full sentence. This turned out to work horribly and was scrapped for Markov Chains. The Markov Chains proved very efficient and capable at generating sentences. It did however reveal that "impurities" in the instructions originally gathered caused strange word choice that detracted from the meaning of the generated recipe instructions.
---
### Next steps
- Use a premium tier of the api to be able to more easily request non duplicate recipes
- Re-clean the data to remove excess commentary.
    -This would include creating a custom list of stopwords
    - Design a cleaning script to standardize units
- Primary goal is to use the models and tools in conjunction with one another
    - KNN modeling would be used to better classify and label foods by training and labeling missing cuisine and dish types 
- A custom Markov Chain trained on better organized instructions cleaned up by reinforcement learning and more implementation of spaCy in defining sentence structure
- Word2Vec in conjunction with KMeans will be used to create replacement mappings from one type of cuisine to another allowing for a marketable “fusion cuisine generator.”
- Finally, I would like to test the model in another field
    - ex) Rework a book from one author’s linguistic type to another’s
