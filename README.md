# Event_Extraction
A biomedical event extraction system by a novel Combination Strategy based on hybrid deep neural networks.   
Online demo: http://www.predictor.xin/event_extraction/ (link deprecated)   
Zhu L, Zheng H. Biomedical event extraction with a novel combination strategy based on hybrid deep neural networks[J]. BMC bioinformatics, 2020, 21(1): 47. https://rdcu.be/b1Pn1
  
## Usage

### Preprocess
(0. The train corpus contains .txt/.a1/.a2 files, placed in `/txt` `/a1` `/a2` directories respectively.)
1. Run `corpus_table.py`, convert .txt/.a1/.a2 files into uniform .csv files (saved in `/table`).
2. Run `a2_preprocess.py`, convert .a2 files into structured .csv files (saved in `/a2_table`).
3. Run `a2_preprocess_modification.py`, convert event modifications in .a2 files into structured .csv files (saved in `/a2_modification_table`).
4. The test corpus should be generated by repeating above process and saved in others directories, e.g. `/table_test`,`/a2_table_test`,`/a2_modification_table_test`.

### Training
1. Run `my_word2vec.py` to generate the pre-trained word vectors (better to modify the code to use a large external corpus). 
2. Run `pretrain_char_cnn.py` to generate the pre-trained character-level CNN.
3. Run `train_net.py` to train the main neural networks, in format `python train_net.py NUMBER` with a argument `NUMBER` which number the trained networks, the trained networks are saved in `/nets`.

### Testing
1. Run `test_generate_strategy_best_ensemble.py` to extract events from testset in `/table_test`, in format `python test_generate_strategy_best_ensemble.py NUM1 NUM2` where `NUM1` denotes the number of ensemble epoches and `NUM2` denotes the number of ensemble training. Meanwhile, the base number for `NUM1` and `NUM2` should be set in codes. The result .a2 files is saved in `/a2_result`.
(1. The `test_generate_event_eval_ensemble.py` is a variation method with same usage.)
2. Use `python BioNLP-evaluation-CG.py -r /GOLDEN_STANDARD_DIR /PARENT_DIR/a2_result/*.a2` to evaluate the performance (for CG).

## Requirements
* Pytorch
* Gensim
* NLTK
* Pandas
* sklearn

TO BE CONTINUED ..
