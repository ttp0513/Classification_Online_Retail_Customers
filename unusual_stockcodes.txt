## StockCode Unusual Codes

##### <li> StockCode is meant to follow the paterrn <strong> [0-9]{5} </strong> but seems to have legit values for <strong> [0-9]{5}[a-zA-Z]+</strong>. It also contains other values as listed below: </li>
| Code | Description | Impact if Included | Action |
| --- | --- | --- | --- |
| ADJUSTX | Looks like manual account adjustments by admins | Not tied to customer purchasing behavior| Exclude |
| AMAZONFEE | Looks like fees for Amazon shipping or something | Not tied to customer purchasing behavior| Exclude | 
| BANK CHARGES or B | Bank charges | Not tied to customer purchasing behavior| Exclude | 
| C2 | Carriage transaction - not sure what this means | Adds noise, not enough data to generalize | Exclude | 
| C3 | Not sure, only 1 transaction | Adds noise, not enough data to generalize |Exclude |
| DCGS | Looks valid, some quantities are negative though and customer ID is null | Can't link to customer profiles | Exclude | 
| D | Looks valid, represents discount values | Can't link to customer profiles | Exclude | 
| DOT | Looks valid, represents postage charges | Can't link to customer profiles| Exclude | 
| gift__XXX | Purchases with gift cards, might be interesting for another analysis, but no customer data | Can't link to customer profiles | Exclude |
| M or m | Looks valid, represents manual transactions | Can't link to customer profiles|  Exclude | 
| PADS | Looks like a legit stock code for padding | Tied to customer purchasing behavior | Include | 
| S | Samples sent to customer | Add noises, Not reflective of actual purchases | Exclude | 
| SP1002 | Looks like a special request item, only 2 transactions, 3 look legit, 1 has 0 pricing | Adds noise, not enough data to generalize | Exclude | 
| TESTXXX | Testing data, not valid | Adds noise, not enough data to generalize | Exclude |

##### Why This Matters?
<li> Outliers and irrelevant data can skew centroids in Customer Segmentation and produce misleading clusters, thus removing them improve the quality and interpretability of customer clusters </li>
