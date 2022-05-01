# Par3
A dataset containing parallel paragraph-level paraphrases

## Dataset Format

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
                    {"gt": [gt_para_1_sent_1],
                    "trans": [[trans_para_1_sent_1]]},
                    {"gt": [gt_para_1_sent_2],
                    "trans": [[trans_para_1_sent_2]]},
                  ],
                  [
                    {"gt": [gt_para_2_sent_1],
                    "trans": [[trans_para_2_sent_1a, trans_para_2_sent_1b]},
                  ],
              ]
          }
      }

}
```

The dataset is pickled dictionary in `par3.pkl`.

`data.keys()` is a list of foreign language novel titles with two-character source language codes appended to them. For example `data[don_quixote_es]` contains the data corresponding to *Don Quixote*, a Spanish novel.

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
