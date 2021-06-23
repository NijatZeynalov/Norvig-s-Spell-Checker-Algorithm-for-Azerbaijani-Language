# Norvig's Spell Checker Algorithm for Azerbaijani Language
The purpose of this project is to prepare a spell checker for Azerbaijani language by implementing a Azerbaijani corpus to Norvig’s algorithm. 

In general, Spell checking tools train through a corpus, train themselves on the correct spelling of words, and in the future, if the word is misspelled, take the correct word in the corpus as a reference. Choosing the right corpus is very important in spell checking, for this purpose I tried several corpuses in the Azerbaijani language available on the Internet, but most of the corpus itself contained such incorrect spelling words. I decided to create a new corpus based on several books written in Azerbaijani. Because, existing corpuses are crawled data and errors may exist. The corpus I created consists of 1478667 words collected from 47 books in 6 fields (biology, geography, detective, literature, encyclopedia, novel).

Although there are several algorithms and methods for spell checking, the most popular and simple of them is the simple logic Spelling Corrector, created by Google employee Peter Norvig. Norvig’s algorithm takes a text or a list of words and separates them word by word, learning the correct spellings for them. To formalize the task of finding most probable correction, it is useful to consider it as a sequence decoding problem. 


Let say w is a received word. Then we’re looking for a word c, out of all possible candidate corrections, that maximizes that c is a desired correction, given the word w:

![a](https://miro.medium.com/max/875/0*ISI-wPj8HdpMdfDi.png)


Using the knowledge of Bayes’ Theorem, we can rewrite this as:

![a](https://miro.medium.com/max/875/1*AbSLByRrVFajAm3KRt7bPg.png)


Since P(w) is the same for every possible candidate c, we can factor it out. Then the four parts of this expression are:

**Selection Mechanism: argmax**
We choose the candidate with the highest combined probability.

**Candidate Model: c ∈ candidates**
This tells us which candidate corrections, c, to consider.

**Language Model: P(c)**
The probability that c appears as a word of English text. For example, occurrences of "the" make up about 7% of English text, so we should have P(the) = 0.07.

**Error Model: P(w|c)**
The probability that w would be typed in a text when the author meant c. For example, P(teh|the) is relatively high, but P(theeexyz|the) would be very low.

Now let's do a few experiments by applying our algorithm to our corpus. Since I plan to apply this algorithm to a medical-related dataset, I address medical questions.

![a](https://miro.medium.com/max/679/1*LAl7TL8sWJU7nvOz_6MPTA.jpeg)

In general, although it can find the right words, in most cases this algorithm makes mistakes. Although the corpus is clean. In this regard, I will try new methods on the same corpus and choose the most accurate.

In conclusion, Peter Norvig’s spell checking algorithm is an easily understandable, simple but an effective algorithm. Although it is originally written for English language, the way it is written enables it to be implemented to other languages with minor modifications
