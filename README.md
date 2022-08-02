# 19BCE1700_NLP_DA2


C:\Users\sriram_sivakumar>python
Python 3.9.6 (tags/v3.9.6:db3ff76, Jun 28 2021, 15:26:21) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.

>>> sentence = "U.S. Citizenship and Immigration Services (USCIS)[3] is an agency of the United States Department of Homeland Security (DHS) that administers the country's naturalization and immigration system. It is a successor to the Immigration and Naturalization Service (INS), which was dissolved by the Homeland Security Act of 2002 and replaced by three components within the DHS: USCIS, Immigration and Customs Enforcement (ICE), and Customs and Border Protection (CBP)."

##1 WORD SEGMENTATION

>>> word_tokenize(sentence)
['U.S', '.', 'Citizenship', 'and', 'Immigration', 'Services', '(', 'USCIS', ')', '[', '3', ']', 'is', 'an', 'agency', 'of', 'the', 'United', 'States', 'Department', 'of', 'Homeland', 'Security', '(', 'DHS', ')', 'that', 'administers', 'the', 'country', "'s", 'naturalization', 'and', 'immigration', 'system', '.', 'It', 'is', 'a', 'successor', 'to', 'the', 'Immigration', 'and', 'Naturalization', 'Service', '(', 'INS', ')', ',', 'which', 'was', 'dissolved', 'by', 'the', 'Homeland', 'Security', 'Act', 'of', '2002', 'and', 'replaced', 'by', 'three', 'components', 'within', 'the', 'DHS', ':', 'USCIS', ',', 'Immigration', 'and', 'Customs', 'Enforcement', '(', 'ICE', ')', ',', 'and', 'Customs', 'and', 'Border', 'Protection', '(', 'CBP', ')', '.']

##2 SENTENCE SEGMENTATION

>>> sent_tokenize(sentence)
['U.S.', "Citizenship and Immigration Services (USCIS)[3] is an agency of the United States Department of Homeland Security (DHS) that administers the country's naturalization and immigration system.", 'It is a successor to the Immigration and Naturalization Service (INS), which was dissolved by the Homeland Security Act of 2002 and replaced by three components within the DHS: USCIS, Immigration and Customs Enforcement (ICE), and Customs and Border Protection (CBP).']

##3 CONVERT TO LOWERCASE

>>> sentence.lower()
"u.s. citizenship and immigration services (uscis)[3] is an agency of the united states department of homeland security (dhs) that administers the country's naturalization and immigration system. it is a successor to the immigration and naturalization service (ins), which was dissolved by the homeland security act of 2002 and replaced by three components within the dhs: uscis, immigration and customs enforcement (ice), and customs and border protection (cbp)."

##4 STOPWORDS REMOVAL

>>> import nltk
>>> from nltk.corpus import stopwords
>>> print(stopwords.words('english'))
['i', 'me', 'my', 'myself', 'we', 'our', 'ours', 'ourselves', 'you', "you're", "you've", "you'll", "you'd", 'your', 'yours', 'yourself', 'yourselves', 'he', 'him', 'his', 'himself', 'she', "she's", 'her', 'hers', 'herself', 'it', "it's", 'its', 'itself', 'they', 'them', 'their', 'theirs', 'themselves', 'what', 'which', 'who', 'whom', 'this', 'that', "that'll", 'these', 'those', 'am', 'is', 'are', 'was', 'were', 'be', 'been', 'being', 'have', 'has', 'had', 'having', 'do', 'does', 'did', 'doing', 'a', 'an', 'the', 'and', 'but', 'if', 'or', 'because', 'as', 'until', 'while', 'of', 'at', 'by', 'for', 'with', 'about', 'against', 'between', 'into', 'through', 'during', 'before', 'after', 'above', 'below', 'to', 'from', 'up', 'down', 'in', 'out', 'on', 'off', 'over', 'under', 'again', 'further', 'then', 'once', 'here', 'there', 'when', 'where', 'why', 'how', 'all', 'any', 'both', 'each', 'few', 'more', 'most', 'other', 'some', 'such', 'no', 'nor', 'not', 'only', 'own', 'same', 'so', 'than', 'too', 'very', 's', 't', 'can', 'will', 'just', 'don', "don't", 'should', "should've", 'now', 'd', 'll', 'm', 'o', 're', 've', 'y', 'ain', 'aren', "aren't", 'couldn', "couldn't", 'didn', "didn't", 'doesn', "doesn't", 'hadn', "hadn't", 'hasn', "hasn't", 'haven', "haven't", 'isn', "isn't", 'ma', 'mightn', "mightn't", 'mustn', "mustn't", 'needn', "needn't", 'shan', "shan't", 'shouldn', "shouldn't", 'wasn', "wasn't", 'weren', "weren't", 'won', "won't", 'wouldn', "wouldn't"]
>>> word_tokens = word_tokenize(sentence)
>>> stopword_removal = [word for word in word_tokens if word not in stopword]
>>> stopword = stopwords.words('english')
>>> print(stopword_removal)
['U.S', '.', 'Citizenship', 'Immigration', 'Services', '(', 'USCIS', ')', '[', '3', ']', 'agency', 'United', 'States', 'Department', 'Homeland', 'Security', '(', 'DHS', ')', 'administers', 'country', "'s", 'naturalization', 'immigration', 'system', '.', 'It', 'successor', 'Immigration', 'Naturalization', 'Service', '(', 'INS', ')', ',', 'dissolved', 'Homeland', 'Security', 'Act', '2002', 'replaced', 'three', 'components', 'within', 'DHS', ':', 'USCIS', ',', 'Immigration', 'Customs', 'Enforcement', '(', 'ICE', ')', ',', 'Customs', 'Border', 'Protection', '(', 'CBP', ')', '.']


##5 STEMMING

>>> from nltk.stem import SnowballStemmer
>>> stopword = stopwords.words('english')
>>> snowball_stemmer = SnowballStemmer('english')
>>> word_tokens = nltk.word_tokenize(sentence)
>>> stem = [snowball_stemmer.stem(word) for word in word_tokens]
>>> print(stem)
['u.', '.', 'citizenship', 'and', 'immigr', 'servic', '(', 'usci', ')', '[', '3', ']', 'is', 'an', 'agenc', 'of', 'the', 'unit', 'state', 'depart', 'of', 'homeland', 'secur', '(', 'dhs', ')', 'that', 'administ', 'the', 'countri', "'s", 'natur', 'and', 'immigr', 'system', '.', 'it', 'is', 'a', 'successor', 'to', 'the', 'immigr', 'and', 'natur', 'servic', '(', 'in', ')', ',', 'which', 'was', 'dissolv', 'by', 'the', 'homeland', 'secur', 'act', 'of', '2002', 'and', 'replac', 'by', 'three', 'compon', 'within', 'the', 'dhs', ':', 'usci', ',', 'immigr', 'and', 'custom', 'enforc', '(', 'ice', ')', ',', 'and', 'custom', 'and', 'border', 'protect', '(', 'cbp', ')', '.']


##6 LEMMATIZATION

>>> from nltk.stem import WordNetLemmatizer
>>> stopword = stopwords.words('english')
>>> wordnet_lemmatizer = WordNetLemmatizer()
>>> word_tokens = nltk.word_tokenize(sentence)
>>> lemmatization = [wordnet_lemmatizer.lemmatize(word) for word in word_tokens]
>>> print(lemmatization)
['U.S', '.', 'Citizenship', 'and', 'Immigration', 'Services', '(', 'USCIS', ')', '[', '3', ']', 'is', 'an', 'agency', 'of', 'the', 'United', 'States', 'Department', 'of', 'Homeland', 'Security', '(', 'DHS', ')', 'that', 'administers', 'the', 'country', "'s", 'naturalization', 'and', 'immigration', 'system', '.', 'It', 'is', 'a', 'successor', 'to', 'the', 'Immigration', 'and', 'Naturalization', 'Service', '(', 'INS', ')', ',', 'which', 'wa', 'dissolved', 'by', 'the', 'Homeland', 'Security', 'Act', 'of', '2002', 'and', 'replaced', 'by', 'three', 'component', 'within', 'the', 'DHS', ':', 'USCIS', ',', 'Immigration', 'and', 'Customs', 'Enforcement', '(', 'ICE', ')', ',', 'and', 'Customs', 'and', 'Border', 'Protection', '(', 'CBP', ')', '.']


##7 PARTS OF SPEECH(POS) TAGGER

>>> words_tagging = nltk.word_tokenize(sentence)
>>> pos_tagging = nltk.pos_tag(words_tagging)
>>> print(pos_tagging)
[('U.S', 'NNP'), ('.', '.'), ('Citizenship', 'NNP'), ('and', 'CC'), ('Immigration', 'NNP'), ('Services', 'NNP'), ('(', '('), ('USCIS', 'NNP'), (')', ')'), ('[', 'VBD'), ('3', 'CD'), (']', 'NN'), ('is', 'VBZ'), ('an', 'DT'), ('agency', 'NN'), ('of', 'IN'), ('the', 'DT'), ('United', 'NNP'), ('States', 'NNPS'), ('Department', 'NNP'), ('of', 'IN'), ('Homeland', 'NNP'), ('Security', 'NNP'), ('(', '('), ('DHS', 'NNP'), (')', ')'), ('that', 'WDT'), ('administers', 'VBZ'), ('the', 'DT'), ('country', 'NN'), ("'s", 'POS'), ('naturalization', 'NN'), ('and', 'CC'), ('immigration', 'NN'), ('system', 'NN'), ('.', '.'), ('It', 'PRP'), ('is', 'VBZ'), ('a', 'DT'), ('successor', 'NN'), ('to', 'TO'), ('the', 'DT'), ('Immigration', 'NNP'), ('and', 'CC'), ('Naturalization', 'NNP'), ('Service', 'NNP'), ('(', '('), ('INS', 'NNP'), (')', ')'), (',', ','), ('which', 'WDT'), ('was', 'VBD'), ('dissolved', 'VBN'), ('by', 'IN'), ('the', 'DT'), ('Homeland', 'NNP'), ('Security', 'NNP'), ('Act', 'NNP'), ('of', 'IN'), ('2002', 'CD'), ('and', 'CC'), ('replaced', 'VBN'), ('by', 'IN'), ('three', 'CD'), ('components', 'NNS'), ('within', 'IN'), ('the', 'DT'), ('DHS', 'NNP'), (':', ':'), ('USCIS', 'NNP'), (',', ','), ('Immigration', 'NNP'), ('and', 'CC'), ('Customs', 'NNP'), ('Enforcement', 'NNP'), ('(', '('), ('ICE', 'NNP'), (')', ')'), (',', ','), ('and', 'CC'), ('Customs', 'NNP'), ('and', 'CC'), ('Border', 'NNP'), ('Protection', 'NNP'), ('(', '('), ('CBP', 'NNP'), (')', ')'), ('.', '.')]
