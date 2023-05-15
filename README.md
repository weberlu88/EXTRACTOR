

# EXTRACTOR

EXTRACTOR helps to extract the system level attack behavior from unstructured threat reports. The extracted attack behavior will be represented in form of directed graphs, where the nodes represent system entities and edges represent system calls. EXTRACTOR leverages Natural Language Processing (NLP) techniques to transform a raw threat report into a graph representation.


## Instructions
### Requirements

This repository uses `python 3.5+` and has the following requirements:
```
nltk == 3.4.5
spaCy == 2.1.0
allennlp == 0.8.4
neuralcoref == 4.0.0
graphviz == 0.13.2
textblob == 0.15.3
pattern == 3.6
numpy == 1.18.1
```
You can directly install the requirements using `pip install -r requirements.txt`
```
1. conda activate Extractor
2. cd C:\Users\weber\Documents\GitHub\EXTRACTOR_OK
3. pip install mysqlclient-1.4.6-cp36-cp36m-win_amd64.whl
4. pip install -r requirements.txt
5. pip install overrides==2.6
6. python -m spacy download en_core_web_lg
7. python -m spacy download en_core_web_sm
8. pip install scikit-learn==0.22
9. pip install jsonnetbin
10. python -m textblob.download_corpora
```


### Usage 

Run EXTRACTOR with `python3 main.py [-h] [--asterisk ASTERISK] [--crf CRF] [--rmdup RMDUP] [--elip ELIP] [--gname GNAME] [--input_file INPUT_FILE]`.

Depending on the usage, each argument helps to provide a different representation of the attack behavior. 
`[--asterisk true]` creates abstraction and can be used to replace anything that is not perceived as IOC/system entity into a wild-card. This representation can be used to be searched within the audit-logs. **Cancel will cause error**.

`[--crf true/false]` allows activating or deactivating of the co-referencing module. 

`[--rmdup true/false]` enables removal of duplicate nodes-edge. 

`[--elip true/false]` is to choose whether to replace ellipsis subjects using the surrounding subject or not.

`[--input_file path/filename.txt]` is to pass the text file to the application. 

`[--gname graph_name]` is to specify the name output graph (two files will be created, e.g., graph.pdf and graph.dot).

#### Example
1. open anaconda prompt
2. conda activate Extractor
3. cd C:\Users\weber\Documents\GitHub\EXTRACTOR_OK
`python main.py --asterisk true --crf true --rmdup true --elip true --input_file input.txt --gname mygraph`
`python main.py --asterisk true --crf true --rmdup true --elip true --input_file DATA_EXEC/Frenk_demo.txt --gname DATA_EXEC/Frenk_demo`
`python main.py --asterisk true --crf true --rmdup true --elip true --input_file DATA_EXEC/Dofloo-SyscallParty.txt --gname DATA_EXEC/Dofloo-SyscallParty`
`python main.py --asterisk true --crf true --rmdup true --elip true --input_file DATA_EXEC/report1_intezer.txt --gname DATA_EXEC/report1_intezer`

## Summarizer
To perform the prediction/text summarization, you need to first convert the `txt` file to the required format `tsv` using `python3 txt2tsv.py`.


### Prediction
To do the extractive summarization, run `python3 prediction.py`


