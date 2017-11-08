Kaggle Author Identification Competition processed by CNN
  Share code and discuss insights to identify horror authors from their writings

https://www.kaggle.com/c/spooky-author-identification


Getting Started

First, get train data from kaggle page(train.csv)

then, split 3 author into each text file(ESP.txt, HPL.txt, MWS.txt)


```
import pandas as pd


if __name__ == "__main__":

    train_df = pd.read_csv("train.csv")
#    train_df.groupby(['text']) 
    EAP = train_df[train_df['author']=='EAP']
    HPL = train_df[train_df['author']=='HPL']
    MWS = train_df[train_df['author']=='MWS']
    ESP_str = EAP.text.astype(str)
    HPL_str = HPL.text.astype(str)
    MWS_str = MWS.text.astype(str)
    ESP_str.to_csv("ESP.txt", index=False)
    HPL_str.to_csv("HPL.txt", index=False)
    MWS_str.to_csv("MWS.txt", index=False)

```

from this, you can get three text files



