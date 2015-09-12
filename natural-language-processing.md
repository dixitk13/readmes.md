#natural-language-processing


# Natural Language Processing - CS6120

This repository caters to the course CS6120 - Natural Language Processing.
### [Compressed English](https://github.com/dixitk13/natural-language-processing/tree/master/CompressedEnglish)
The OpenFST package is used for compressed English and building finite-state machines.
##### Unvoweler && Inverted Unvoweler :
Transducer that removes the vowels aeiou (not y) from any string of the 26 lowercase letters and space.
##### Squasher && Inverted Squasher : 
Transducer to leave the first and last characters of each word alone, and remove only internal vowels.

#### [Prounouncing Numbers](https://github.com/dixitk13/natural-language-processing/tree/master/ProunouncingNumbers)
A transducer that maps numbers in the range 0 - 999,999,999 represented as digit strings to their English read form, e.g.:

     1 -> one
     1 1 -> eleven
     1 1 1 -> one hundred eleven
     1 1 1 1 -> one thousand one hundred eleven
     1 1 1 1 1 -> eleven thousand one hundred eleven

### [Formal Semantics](https://github.com/dixitk13/natural-language-processing/tree/master/FormalSemantics)
Deals with quantified formulas of first-order logic and λ-abstracts.

### [Word Alignment](https://github.com/dixitk13/natural-language-processing/tree/master/WordAlignment)
Inversion transduction grammar is a special case of synchronous context-free grammar. Furthermore, a special case of ITG is a bracketing transduction grammar (BTG), which has only one nonterminal. The Word Alignment project implements the algorithm from [Dekai Wu's original paper from Computational Linguistics in 1997](http://aclweb.org/anthology-new/J/J97/J97-3002.pdf).

[test.en](http://www.ccs.neu.edu/course/cs6120sp15/test.en): 100 short English sentences, from the European Parliament corpus.

[test.de](http://www.ccs.neu.edu/course/cs6120sp15/test.de): German translations of those 100 sentences.

[itg.dict](http://www.ccs.neu.edu/course/cs6120sp15/itg.dict): a probabilistic translation dictionary grammar. 

The Aligner finds best word alignment for each sentence pair, given the grammar and dictionary like so : 

```sh
that was not the intention at doha . ==>  das war nicht die absicht von doha .
```
```sh
 [ [[that]/[das],[was]/[war]] , [ [[not]/[nicht],[the]/[die]] , [[intention]/[absicht], [[<Epsilon>]/[von], [[at]/[<Epsilon>], [[doha]/[doha],[.]/[.]] ] ] ] ] ] 
```
### [ChomskyNormalForm](https://github.com/dixitk13/natural-language-processing/tree/master/ChomskyNormalForm)
A probabilized generation program which start with the START symbol and recursively choose rewrite rules until termination. Each rule is preceded by a non-negative real number. This number is used to determine the probability and the rule is choosen.

The context free grammar is of the form :
```sh
  i.  A -> B C
 ii.  A -> B
iii.  A -> a
where A, B, C are non-terminals, a are terminals
```
The program  consists of two parts:
###### Grammar Parsing: 
The Grammar is Parsed by the module ChomskyNormalForm which organises it into tuples and keeps track of the probability for one run.
###### Sentence Generation: 
The ChomskyNormalFormGenerator is responsible to take this grammar as input and then forms sentences according to the probability and results in different output's on every run.

The [sample output](https://github.com/dixitk13/natural-language-processing/tree/master/ChomskyNormalForm) and the [grammar files](https://github.com/dixitk13/natural-language-processing/tree/master/ChomskyNormalForm).

### [Literature](https://github.com/dixitk13/natural-language-processing/tree/master/Literature)
This paper talks about a few conversant systems which participated in the Loebner con-
test. The Loebner contest being the instantiation of the Turing test, how it encourages
programmers to improve the state of the art in Natural Language Processing and Computational intelligence. It describes the evolution, design issues, computational model and successful techniques employed in the making of conversant systems using Natural Language Processing (NLP), Markov Models and dedicated technology such as AIML/ChatScript.

###### Keywords
Conversant systems, Loebner contest, Turing test, Chat-bot, ELIZA, PARRY,
SHRDLU, MegaHAL, Jabberwacky, ALICE, Suzette, AIML

### Version
1.0

created using : [Dillinger](http://dillinger.io/)