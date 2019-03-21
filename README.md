# Page-Ranking-Software
Build a basic search engine or document retrieval system using Vector space model. This use case is widely used in information retrieval systems. Given a set of documents and search term(s)/query we need to retrieve relevant documents that are similar to the search query. 

![alt text](https://3.bp.blogspot.com/-w96aVPMy198/WfgQTqkmI7I/AAAAAAAAGAQ/zd3iZfVh0_E5Yy2d_1WSs5N8RB8rPJRbwCK4BGAYYCw/s1600/information%2Bretrieval_1.PNG)

# Vector Space Model:
A vector space model is an algebraic model, involving two steps, in first step we represent the text documents into vector of words and in second step we transform to numerical format so that we can apply any text mining techniques such as information retrieval, information extraction,information filtering etc.

Let us understand with an example. consider below statements and a query term. The statements are referred as documents hereafter.
Document 1: Cat runs behind rat
Document 2: Dog runs behind cat
Query: rat

# Document vectors representation:
In this step includes breaking each document into words, applying preprocessing steps such as removing stopwords, punctuations, special characters etc. After preprocessing the documents we represent them as vectors of words. 
Below is a sample representation of the document vectors.
Document 1: (cat, runs, behind, rat)
Document 2: (Dog, runs, behind, cat)
Query: (rat)

the relevant document to Query = greater of (similarity score between (Document1, Query), similarity score between (Document2, Query)

Next step is to represent the above created vectors of terms to numerical format known as term document matrix. 

# Term Document Matrix:
A term document matrix is a way of representing documents vectors in a matrix format in which each row represents term vectors across all the documents and columns represent document vectors across all the terms. The cell values frequency counts of each term in corresponding document. If a term is present in a document, then the corresponding cell value contains 1 else if the term is not present in the document then the cell value contains 0.

After creating the term document matrix, we will calculate term weights for all the terms in the matrix across all the documents. It is also important to calculate the term weightings because we need to find out terms which uniquely define a document. 

We should note that a word which occurs in most of the documents might not contribute to represent the document relevance whereas less frequently occurred terms might define document relevance. This can be achieved using a method known as term frequency - inverse document frequency (tf-idf), which gives higher weights to the terms which occurs more in a document but rarely occurs in all other documents, lower weights to the terms which commonly occurs within and across all the documents.
Tf-idf = tf X idf 
tf = term frequency is the number of times a term occurs in a document
idf = inverse of the document frequency, given as below
idf = log(N/df), where df is the document frequency-number of documents containing a term

![alt text](https://1.bp.blogspot.com/-mAM6NJ4bEoE/WfgfF2OfLII/AAAAAAAAGAs/axKBhPnJzR8W3QAEqNGf5ymiXpDg3JATgCK4BGAYYCw/s1600/information%2Bretrieval_3.PNG)

![alt text](https://1.bp.blogspot.com/-crJGbyKFrVE/Wfgfhr3goWI/AAAAAAAAGA4/-s20-N7rNo44P_bTVeQ3idfSDR8byVyBwCK4BGAYYCw/s1600/information%2Bretrieval_term%2Bdocument%2Bmatrix.PNG)

![alt text](https://4.bp.blogspot.com/-tFQtMLUhGe4/Wfgf5itrTEI/AAAAAAAAGBA/W6YV8hXsI5QgHjIkwmjhLdQPnQyjh9iuQCK4BGAYYCw/s1600/information%2Bretrieval_inverse_document_frequency.PNG)

![alt text](https://3.bp.blogspot.com/-dUNMClK9RkQ/WfggZdjH6dI/AAAAAAAAGBM/rC7SE_3fzLUjBFjwytpaGmPflFns8t3dwCK4BGAYYCw/s1600/tf_idf_term_document_matrix.PNG)

![alt text](https://4.bp.blogspot.com/-iK-fPUBaCJw/WfquoRa2XSI/AAAAAAAAGCU/xISB9LksuyQBmMIIzLIbuJ-RhMob5WDRwCK4BGAYYCw/s1600/term_frequency_variants.PNG)

![alt text](https://4.bp.blogspot.com/-YIotvRU0ObE/WfqvC548rPI/AAAAAAAAGCc/ewk6WlZ2zmUhp47xe3p8jKwvU6cyq12TACK4BGAYYCw/s1600/inverse_document_frequency_variants.PNG)


# Similarity Measures: cosine similarity
Mathematically, closeness between two vectors is calculated by calculating the cosine angle between two vectors. In similar lines, we can calculate cosine angle between each document vector and the query vector to find its closeness. To find relevant document to the query term , we may calculate the similarity score between each document vector and the query term vector by applying cosine similarity . Finally, whichever documents having high similarity scores will be considered as relevant documents to the query term.

When we plot the term document matrix, each document vector represents a point in the vector space. In the below example query, Document 1 and Document 2 represent 3 points in the vector space. We can now compare the query with each of the document by calculating the cosine angle between them. 

![alt text](https://2.bp.blogspot.com/-saTZSoc5RAA/WfghS_CMvJI/AAAAAAAAGBg/PcZvT0QNZCcPJq8fAv2v_cSwrnagdm9RgCK4BGAYYCw/s1600/cosine_similarity.PNG)
