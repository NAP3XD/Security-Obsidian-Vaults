### Export2PDF
```
jupyter nbconvert --to pdf your_notebook.ipynb

// if not working
pip install nbconvert jupyter jupyterlab_pygments
sudo apt install texlive-full

```
## Pandas
#pandas

### Log Enrich

Use Jupyter notebook. 
.ipynb   
```
%pip install --upgrade pip
%pip install pandas
import pandas as pd
import json
import sys

NetFlo_df = pd.DataFrame()   // create dataFrame

NetFlo_df = pd.read_json("nflog.json", lines=True)  // read in Json
NetFlo_df

// crt new col by running a function on another 
NetFlo_df["<newCol>"] = NetFlo_df["ExistingCol"].apply(<function2Apply>)

NetFlo_df.head(50)

NetFlo_df.to_json('enriched_netFlow_log.json', orient='records', lines=True) // exporting to json (real world)
df.to_json("enriched_logs.csv", index=False) // export log 2 json (unused)
df.to_csv("enriched_logs.csv", index=False)  // export log 2 csv
```