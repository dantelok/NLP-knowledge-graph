# NLP-knowledge-graph

Data Source
The articles from HSBC website 

Step 1：Grab the text on the example url
Find the article in https://insights.hsbc.co.uk/content/hsbc/gb/en_gb/wealth/insights/macro-outlook/china-insights/china-insights-2019-09-11/
In this html file, clean up some taggings and extract useful information (the content of the article)
I got some tabs content in the header and footer, but removed them in the dataframe
Finally, I splitted the sentences from the whole article and make a list of sentences.


Step 2：Text pre-processing
In the pre-processing procedure, I set some basic rules to make the text format consistent.
For example, convert all text in lowercase, remove space and stemming.
I didn't remove numbers and punctuation here because there are some percentage numbers in the article.
After the pre-processing, I generate a list of words for POS tagging.


Step 3：Visualize the text tree
Construct the tree of text and make sure the POS tagging and the dependency going a right direction.
We can also visualize the relationship with layer.


Step 4：Name Entities Recognition
By using spacy, build up a NLP model with 'en_core_web_sm'.
Put the passage in the model and process NER (Name Entities Recognition).
Finally generate the label and dependency of each entity.


Step 5：Recognize the name entities using the whole article
Using the spacy displacy function to recognize all dependency and name entities' label.


Step 6：set up a get_entities and get_relation function to get the nodes and edge of the knowledge graph
(1) get_entities
In this function, get the names from the sentence.
I do some checkings on whether it's compound noun or modifier here, to make sure not missing a part of the name.
Then identify the subject and object and put them into a list.

(2) get_relation
In this function, get the dependency pattern and match the entities we've found above.


Step 7：Construct the knowledge graph
Set up a dataframe to store the nodes and edge of the graph.
Draw the knowledge graph with the Network library
