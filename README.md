uniparser-grammar-meadow-mari
=============================

This is a formalized description of literary Meadow Mari morphology, which also includes a number of dialectal elements. The description is carried out in the UniParser format and involves a description of the inflection (paradigms.txt), a grammatical dictionary (mhr_lexemes_XXX.txt files) and a short list of analyses that should be avoided (bad_analyses.txt). The dictionary contains descriptions of individual lexemes, each of which is accompanied by information about its stem, its part-of-speech tag and some other grammatical/borrowing information, its inflectional type (paradigm), and Russian translation.

This description can be used for morphological analysis of Meadow Mari texts in the following ways:

1. The simplest solution is to a pre-analyzed wordlist for analyzing your texts. The ``wordlists`` directory contains frequency lists of tokens based on Meadow Mari corpora. The first set of lists (``_main``) comes from the standard corpus that contains 2.63 million words in mass media, Wikipedia articles and the like. The second (``_social_media``) comes from a 4-million-word corpus of social media in Meadow Mari, which contains many instances of dialectal forms and inconsistent spelling. In both sets, relaxed mode was used: the diacritics were not taken into account. Each set consists of a tab-delimited list of word forms and their frequencies (``wordlist``), a list of analyzed word forms (``parsed``; one word form with analyses in XML per line) and a list of unanalyzed word forms (``unanalyzed``). The recall of the analyzer on the standard corpus texts (in tokens) is about 91%; recall on non-standard texts is lower.

2. The ``analyzer`` directory contains the UniParser set of scripts together with all necessary language files. You can use it to analyze your own frequency word list. Your have to name your list "wordlist.csv" and put it to that directory. Each line should contain one token and its frequency, tab-delimited. When you run analyzer/UniParser/analyze.py, the analyzer will produce two files, one with analyzed tokens, the other with unanalyzed ones. (You can also use other file names and separators with command line options, see the code of ``analyze.py``.) This way, you will notbe restricted by my word list, but the analyzer works pretty slowly (300-400 tokens per second). If you want to make changes to the dictionaries, run the finalizer script in the ``finalizer`` directory when you are done. It will produce a new unified ``lexemes.txt`` file and add diacriticless stem variants there, put these to the ``analyzer`` directory. If you would prefer to suppress the diacriticless variants (i.e. your texts are 100% clean and spelled correctly), you will have to switch this function off, e.g. by editing the ``russify`` function in the finalizer script.

3. Finally, you are free to convert/adapt the description to whatever kind of morphological analysis you prefer to use.

This software is distributed under the MIT license (see LICENSE.md).
