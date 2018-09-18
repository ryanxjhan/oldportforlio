---
layout: mypost
title: Permutation Importance
categories: [Feature Engineering]
---

### Model
- Load the data
- Divide the data into training and validation
- Build a model that predicts taxi fares
- Print a few rows for you to review


```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

data = pd.read_csv('FIFA 2018 Statistics.csv')
y = (data['Man of the Match'] == "Yes")  # Convert from string "Yes"/"No" to binary
feature_names = [i for i in data.columns if data[i].dtype in [np.int64]]
X = data[feature_names]
train_X, val_X, train_y, val_y = train_test_split(X, y, random_state=1)
my_model = RandomForestClassifier(random_state=0).fit(train_X, train_y)
```

### Permutation Importance
**[eli5](https://eli5.readthedocs.io/en/latest/) library**


```python
import eli5
from eli5.sklearn import PermutationImportance

perm = PermutationImportance(my_model, random_state=1).fit(val_X, val_y)
eli5.show_weights(perm, feature_names = val_X.columns.tolist())
```





    <style>
    table.eli5-weights tr:hover {
        filter: brightness(85%);
    }
</style>



    

    

    

    

    

    


    

    

    

    

    

    


    

    

    

    

    
        <table class="eli5-weights eli5-feature-importances" style="border-collapse: collapse; border: none; margin-top: 0em; table-layout: auto;">
    <thead>
    <tr style="border: none;">
        <th style="padding: 0 1em 0 0.5em; text-align: right; border: none;">Weight</th>
        <th style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">Feature</th>
    </tr>
    </thead>
    <tbody>
    
        <tr style="background-color: hsl(120, 100.00%, 80.00%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0750
                
                    &plusmn; 0.1159
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Goal Scored
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 82.40%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0625
                
                    &plusmn; 0.0791
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Corners
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 86.29%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0437
                
                    &plusmn; 0.0500
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Distance Covered (Kms)
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 87.69%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0375
                
                    &plusmn; 0.0729
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                On-Target
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 87.69%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0375
                
                    &plusmn; 0.0468
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Free Kicks
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 92.42%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0187
                
                    &plusmn; 0.0306
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Blocked
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 94.29%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0125
                
                    &plusmn; 0.0750
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Pass Accuracy %
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 94.29%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0125
                
                    &plusmn; 0.0500
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Yellow Card
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 96.49%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0063
                
                    &plusmn; 0.0468
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Saves
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 96.49%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0063
                
                    &plusmn; 0.0250
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Offsides
            </td>
        </tr>
    
        <tr style="background-color: hsl(120, 100.00%, 96.49%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0063
                
                    &plusmn; 0.1741
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Off-Target
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 100.00%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0.0000
                
                    &plusmn; 0.1046
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Passes
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 100.00%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0
                
                    &plusmn; 0.0000
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Red
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 100.00%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0
                
                    &plusmn; 0.0000
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Yellow &amp; Red
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 100.00%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                0
                
                    &plusmn; 0.0000
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Goals in PSO
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 89.16%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                -0.0312
                
                    &plusmn; 0.0884
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Fouls Committed
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 87.69%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                -0.0375
                
                    &plusmn; 0.0919
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Attempts
            </td>
        </tr>
    
        <tr style="background-color: hsl(0, 100.00%, 84.94%); border: none;">
            <td style="padding: 0 1em 0 0.5em; text-align: right; border: none;">
                -0.0500
                
                    &plusmn; 0.0500
                
            </td>
            <td style="padding: 0 0.5em 0 0.5em; text-align: left; border: none;">
                Ball Possession %
            </td>
        </tr>
    
    
    </tbody>
</table>
    

    


    

    

    

    

    

    







### Credit

[Kaggle](https://www.kaggle.com/dansbecker/permutation-importance)
