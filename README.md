# Par3
A dataset containing parallel paragraph-level paraphrases

## Dataset Examples

### Paragraph-level Alignments
Source paragraph:  
>Вронский понял, что дальнейшие попытки тщетны и что надо пробыть в Петербурге эти несколько дней, как в чужом городе, избегая всяких сношений с прежним светом, чтобы не подвергаться неприятностям и оскорблениям, которые были так мучительны для него. Одна из главных неприятностей положения в Петербурге была та, что Алексей Александрович и его имя, казалось, были везде. Нельзя было ни о чем начать говорить, чтобы разговор не свернулся на Алексея Александровича; никуда нельзя было поехать, чтобы не встретить его. Так по крайней мере казалось Вронскому, как кажется человеку с больным пальцем, что он, как нарочно, обо все задевает этим самым больным пальцем.

Google Translate paragraph:
>Vronsky realized that further attempts were in vain and that he had to stay in Petersburg for these few days, as in a strange city, avoiding all relations with the old world, so as not to be exposed to the troubles and insults that were so painful for him. One of the main troubles of the situation in St. Petersburg was that Alexey Alexandrovich and his name seemed to be everywhere. It was impossible to start talking about anything, lest the conversation turned to Alexey Alexandrovich; it was impossible to go anywhere without meeting him. So at least it seemed to Vronsky, as it seems to a man with a sore finger, that he, as if on purpose, was touching everything with that sore finger.

Translator 1 paragraph:  
>Vronsky understood that further attempts were futile and that they would have to spend those few days in Petersburg as in a foreign city, avoiding all contacts with their former society so as not to be subjected to insults and unpleasantnesses, which were so painful for him. One of the most unpleasant things about the situation in Petersburg was that Alexei Alexandrovich and his name seemed to be everywhere. It was impossible to begin talking about anything without the conversation turning to Alexei Alexandrovich; it was impossible to go anywhere without meeting him. At least it seemed so to Vronsky, as it seems to a man with a sore finger that he keeps knocking into everything, as if on purpose, with that finger.

Translator 2 paragraph:  
>Vronsky realized that further attempts were futile and that he must spend these few days in Petersburg as if it were a foreign city, avoiding all dealings with his former world in order to avoid being subjected to unpleasant and insulting treatment, which would be agonizing for him. One of the most unpleasant aspects of his situation in Petersburg was the fact that Alexei Alexandrovich and his name seemed to be everywhere. You could not begin talking about anything without the conversation turning to Alexei Alexandrovich; you could not go anywhere without encountering him. Or so at least it seemed to Vronsky, as it seems to someone with a sore toe that he is constantly stubbing this same sore toe, as if on purpose.

### Sentence-level Alignments
Currently, the sentence-level alignments are for Google Translated text and human translations *only*. There is no alignment with the source language sentences, which would require multilingual sentence tokenization. Additionally, sentence-level alignments are independent for each Google Translate-human translation pair. So, 4 aligned sentences for GT-translator_1 does not imply that there are 4 aligned sentences for GT-translator_2, which could have fewer or more aligned sentences. Each translator has made their own decisions about merging or splitting sentences from the source text, so each paragraph in an alignment may not have the same number of sentences.

Here's a nice case of sentence alignment where a three-way alignment can be found between Google Translate, Translator 1, and Translator 2.

Google Translate sentence:
> “For a long time Anna Pavlovna has not been with us,” the princess said once about Petrova.

Translator 1 sentence:
>‘It’s some while since Anna Pavlovna has visited us,’ the princess said once of Petrov’s wife.

Translator 2 sentence:
“I wonder why Anna Pavlovna has not been to see us for so long,” the princess said once about Madame Petrova.

Here's a case in which Translator 1 presumably merged 2 sentences from the source text.

Translator 1 sentence:
>‘No, just do as I told you,’ he said, softening the remark with a smile, and after briefly explaining the matter as he understood it, he pushed the papers aside, saying: ‘Do it that way, please, Zakhar Nikitich.’

Google Translate (for Translator 1) sentences:
> “No, you do as I said,” he said, softening the remark with a smile, and, briefly explaining to him how he understood the matter, pushed the papers aside and said: “Do so, please.

>So please, Zakhar Nikitich.

Translator 2 sentence:
>“No, do it the way I told you,” he said, softening his remark with a smile, and after briefly explaining how he understood the case, pushed the papers away and said, “So do it that way, please.

Google Translate (for Translator 2) sentence:
> “No, you do as I said,” he said, softening the remark with a smile, and, briefly explaining to him how he understood the matter, pushed the papers aside and said: “Do so, please.

Here's a case in which both translators presumably split 1 sentence from the source text.

Google Translate sentence:
> “I don’t express my opinion about either education,” Sergei Ivanovich said with a smile of condescension, like a child, putting his glass in, “I’m just saying that both sides have strong arguments,” he continued, turning to Alexei Alexandrovich.

Translator 1 sentences:
>‘I am not expressing my opinion about either sort of education,’ Sergei Ivanovich said with a smile of condescension, as if to a child, and held out his glass.

>‘I am merely saying that there are strong arguments on both sides,’ he went on, turning to Alexei Alexandrovich.

Translator 2 sentences:
>“I am not expressing my own opinion about any particular culture,” said Sergei Ivanovich with a smile of condescension, as if for a child, as he offered his glass.

>“I am merely saying that both sides have powerful arguments,” he continued, addressing Alexei Alexandrovich.

## Dataset Details
The dataset is pickled dictionary in `par3.pkl`.

We provide the script `sample_par3.pkl` to demonstrate how to access paragraph and sentence alignments in Par3.

### Accessing Paragraph Alignments
https://github.com/ngram-lab/par3/blob/bb42d319c6e313383a1594e8e3367811c3efa2ea/sample_par3.py#L8 specifies a book from which to randomly sample a paragraph.
https://github.com/ngram-lab/par3/blob/bb42d319c6e313383a1594e8e3367811c3efa2ea/sample_par3.py#L11 stores all source paragraphs for that book in the variable `source_paras`.
https://github.com/ngram-lab/par3/blob/bb42d319c6e313383a1594e8e3367811c3efa2ea/sample_par3.py#L14 stores all source paragraphs for that book in the variable `gt_paras`.
https://github.com/ngram-lab/par3/blob/bb42d319c6e313383a1594e8e3367811c3efa2ea/sample_par3.py#L17 stores all source paragraphs for that book in the variable `translator_data`.
`translator_data` is a dictionary containing data for each human translation of the source text. Each translation's data can be accessed with the key `translator_i`, where `i` is the number of the translation.
https://github.com/ngram-lab/par3/blob/bb42d319c6e313383a1594e8e3367811c3efa2ea/sample_par3.py#L24-L25 demonstrate how to access the paragraphs for each human translation that correspond to `source_paras` and `gt_paras`.

### Accessing Sentence Alignments
Note that in the following line
https://github.com/ngram-lab/par3/blob/0fe6e037262fc3097e3214e672de5352c603acfe/sample_par3.py#L32
we iterate over each human translator's data because sentence-level alignments are independent for each Google Translate-human translation pair.

https://github.com/ngram-lab/par3/blob/0fe6e037262fc3097e3214e672de5352c603acfe/sample_par3.py#L34 usually stores a singleton list of the first sentence by `translator_i` in the randomly sampled paragraph from above. However, it's possible that this list contains more than one sentence.
https://github.com/ngram-lab/par3/blob/0fe6e037262fc3097e3214e672de5352c603acfe/sample_par3.py#L35-L36

Similarly, we access the corresponding Google Translation sentence(s) for `translation_i`.
https://github.com/ngram-lab/par3/blob/0fe6e037262fc3097e3214e672de5352c603acfe/sample_par3.py#L38-L40

### Dataset Structure  
```
{
   "book_title": {
      "source_paras": [source_para_1,source_para2],
      "gt_paras": [gt_para_1, gt_para2],
      "translator_data": {
          "translator_1": {
              "translator_paras": [trans1_para_1, trans2_para_2],
              "sent_alignments": [
                  [
                    {"gt": [[gt_para_1_sent_1]],
                    "trans": [[trans_para_1_sent_1]]},
                    {"gt": [[gt_para_1_sent_2]],
                    "trans": [[trans_para_1_sent_2]]},
                  ],
                  [
                    {"gt": [[gt_para_2_sent_1]],
                    "trans": [[trans_para_2_sent_1a, trans_para_2_sent_1b]},
                  ],
              ]
          }
      }

}
```

`data.keys()` is a list of foreign language novel titles with two-character source language codes appended to them. For example `data["don_quixote_es"]` contains the data corresponding to *Don Quixote*, a Spanish novel.

`data[title_langcode]` is a dictionary with 3 keys:
1. `"source_paras"`
2. `"gt_paras"`
3. `"translator_data"`

`data[title_langcode]["source_paras"]` is a list of paragraphs in the source language. `data[title_langcode]["gt_paras"]` is a list of the *same length* as `data[title_langcode]["source_paras"]` that contains the corresponding paragraph from Google Translate. Therefore, `data[title_langcode]["source_paras][x]"` is aligned with `"data[title_langcode][gt_paras][x]"`.

`data[title_langcode]["translator_data"]` is a dictionary with `n` keys in the format `translator_i`, where `n` is between 2 and 5 and represents the number of different English translations included for a specific source text.

`data[title_langcode]["translator_data"][translator_i]` is a dictionary with 2 keys:
1. `"translator_paras"`
2. `"sent_alignments"`

`data[title_langcode]["translator_data"][translator_i]["translator_paras"]` is analogous to `data[title_langcode]["source_paras"]` and `data[title_langcode]["gt_paras"]`. It is a list of the same length as `data[title_langcode]["source_paras"]` For any index `x`, `data[title_langcode]["translator_data"][translator_i]["translator_paras"][x]` is aligned with `data[title_langcode]["source_paras"][x]` and `data[title_langcode]["gt_paras"][x]`.

`data[title_langcode]["translator_data"][translator_i]["sent_alignments"]` is a list of lists the same length as `data[title_langcode]["source_paras"]`. Each list corresponds to one paragraph and contains a list of dictionaries. The number of dictionaries is equal to the number of sentences in that paragraph. The `"gt"` key is a list of the Google Translate sentence(s), while the `"trans"` key is a list of the corresponding transltor sentence(s). Note that these two lists need not be the same length in the case that sentences within a paragraph were split or merged by different translators.
