# Natural Language Processing (NLP)

## Top-terms classifier

```python
>>> from sklearn.datasets import fetch_20newsgroups
>>> from sklearn.feature_extraction.text import CountVectorizer
>>> import xam

>>> cats = ['alt.atheism', 'comp.windows.x']
>>> newsgroups_train = fetch_20newsgroups(subset='train', categories=cats)
>>> newsgroups_test = fetch_20newsgroups(subset='test', categories=cats)

>>> vectorizer = CountVectorizer(stop_words='english', max_df=0.2)

>>> X_train = vectorizer.fit_transform(newsgroups_train.data)
>>> y_train = newsgroups_train.target

>>> X_test = vectorizer.transform(newsgroups_test.data)
>>> y_test = newsgroups_test.target

>>> clf = xam.nlp.TopTermsClassifier(n_terms=50)
>>> clf.fit(X_train.toarray(), y_train).score(X_test.toarray(), y_test)
0.95238095238095233

```
