# MatchSum - Processed Generation Results
We process the generation results for MATCHSUM: ACL 2020 paper: *[Extractive Summarization as Text Matching](https://arxiv.org/abs/2004.08795)*. The generated results are released in the official repo: https://github.com/maszhongming/MatchSum. We process the results for CNNDM and XSUM. Relied on the datasets released by HuggingFace, we compare the generation results for MATCHSUM and generate the following files:
- ```test.source```: contains the input document
- ```test.target```: contains the headline, which serves as the ground truth for summarization task
- ```test_generations.txt```: contains the generation results from MATCHSUM

Here are the links to download the HuggingFace dataset:
- CNN/DM: https://cdn-datasets.huggingface.co/summarization/cnn_dm_v2.tgz
- XSUM: https://cdn-datasets.huggingface.co/summarization/xsum.tar.gz

```bash
matchsum
 |-- cnndm
 |    |--test.source
 |    |--test.target
 |    |--test_generations.txt
 |-- xsum
 |    |--test.source
 |    |--test.target
 |    |--test_generations.txt
 |
```

## Note
By comparing the testing set released by HuggingFace, there are the following points to note:
- Testing set from HuggingFace for CNN/DM contains 11490 documents, while the testing set from MATCHSUM contains 11489 documents. So in the released ```test.source```, ```test.target```, and ```test_generation.txt``` have 11489 observations which are consistent with the official results for MATCHSUM. 
  - There is one observation in HuggingFace test set which is missing from MATCHSUM test set. 

```
Document:
The build-up for the blockbuster fight between Floyd Mayweather and Manny Pacquiao in Las Vegas on May 2 steps up a gear on Tuesday night when the American holds an open workout for the media. The session will be streamed live across the world and you can watch it here from 12am UK (7pm EDT).

Target:
Floyd Mayweather holds an open media workout from 12am UK (7pm EDT) The American takes on Manny Pacquiao in Las Vegas on May 2 . Mayweather's training is being streamed live across the world .
```

- Here the results for CNN/DM use the generation results from ```MatchSum_RoBERTa```.

- Testing set from HuggingFace for XSUM contains 11333 documents, while the testing set from MATCHSUM contains 11332 documents. So in the released ```test.source```, ```test.target```, and ```test_generation.txt``` have 11332 observations which are consistent with the official results for MATCHSUM. 

  - There are two observations in HuggingFace test set which are missing from MATCHSUM test set.
  
```
Document #1: More to follow

Target #1: Carl Frampton suffered the first defeat of his professional career as Leo Santa Cruz won on points to regain the WBA featherweight title in Las Vegas.

Document #2: Causanagh Road, LoughgallTannyoky Road, PoyntzpassCarrowreagh Road, DundonaldEdenticullo Road, HillsboroughNew Line Road, RathfrilandDrumanure Road, Derrygonnelly

Target #2: These roads in Northern Ireland are closed due to poor weather conditions as of Friday 15 January.
```

  - There is one observation in MATCHSUM test set which is missing from HuggingFace test set.

```
Reference: here is the full text of theresa may's letter to european council president donald tusk, beginning the start of brexit negotiations.

Summary: the bbc said there are no current plans to broadcast a spin-off series . lord sugar added that the success of previous apprentice winners was "what motivates me to carry on doing -lsb- the show -rsb- ".
```

- The generation results ```test_generation.txt``` is lowercased, which is consistent with the released results for MATCHSUM. Both ```test.source``` and ```test.target``` are from HuggingFace.

- We also clean out some prefix like ```-lrb-```, ```-rrb-```, ```-lsb-``` and ```-rsb-```.
