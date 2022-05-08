# Neural Network Charity Analysis

## Introduction

Over the past 20 years Alphabet Soup has donated over 10 Billion to different agencies. Some of the money donated went to helping develop life saving technology. Some of the money donated went to climate efforts like forest reforestation. Alphabet Soup's president, Andy Glad, has asked Beks to review the avaiable data and try to help develop a way to determine if an agency is valid and the money donated from Alphabet Soup will be properly utilized.   

From Alphabet Soup’s business team, Beks received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as the following:

- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

## Analysis of dataset

### Preparing the data

The first step to preparing the data is to read the data in from the CSV file we were provided, and get it loaded  into a dataframe.

<img src="Resources/original_data.png">

The next step is to start the cleansing by removing data columns which are not necessary or important to the analysis. In the case of this dataset we drop the two columns, EIN and NAME, which are identifier columns.

<img src="Resources/original_data_cleaning.png">

The next step of the data prep is to encode the string data into usable values, 1 or 0.  The encoding process produces a dataset which looks like:
 
<img src="Resources/original_data_encoding.png">

Now that we have cleansed dataset, we are ready to start building our neural network and start the analysis process. We setup our first network with the following parameters:

<table>
<tr>
<th>Layer</th>
<th>Nodes</th>
<th>Activation</th>
</tr>
<tr>
<td>1</td>
<td>10</td>
<td>relu</td>
</tr>
<tr>
<td>2</td>
<td>5</td>
<td>relu</td>
</tr>
<tr>
<td>output</td>
<td></td>
<td>sigmoid</td>
</tr>
</table>

<img src="Resources/original_setup.png">

After training this model by running it through 100 epochs, the model showed an accuracy of 72.45%. 

<img src="Resources/original_results.png">

While 72.45% is not a bad rate of accuracy, it is not good enough for our purposes. So we decided to rebuild the model and try to optimize it in different ways to see if we could improve the accuracy.

## Optimization Attempts

The first attempt of optimization for the model was to try to utilize the same model but with larger number of nodes for the two hidden layers.

<table>
<tr>
<th>Layer</th>
<th>Nodes</th>
<th>Activation</th>
</tr>
<tr>
<td>1</td>
<td>20</td>
<td>relu</td>
</tr>
<tr>
<td>2</td>
<td>10</td>
<td>relu</td>
</tr>
<tr>
<td>output</td>
<td></td>
<td>sigmoid</td>
</tr>
</table>

<img src="Resources/optimization1_setup.png">

After training this model by running it through 100 epochs, the model showed an accuracy of 72.65%. A small improvement, but no where near the kind of improvement we need to utilize the model.

<img src="Resources/optimization1_results.png">

The second attempt of optimization for the model was to try to utilize the same model but with new activations for the two hidden layers.

<table>
<tr>
<th>Layer</th>
<th>Nodes</th>
<th>Activation</th>
</tr>
<tr>
<td>1</td>
<td>20</td>
<td>tanh</td>
</tr>
<tr>
<td>2</td>
<td>10</td>
<td>tanh</td>
</tr>
<tr>
<td>output</td>
<td></td>
<td>sigmoid</td>
</tr>
</table>

<img src="Resources/optimization2_setup.png">

After training this model by running it through 100 epochs, the model showed an accuracy of 72.47%. A small decrease in accuracy. Better than the original marginally, but not better than just adding nodes to the original. This is obviously not the accuracy we need to utilize the model.

<img src="Resources/optimization2_results.png">

The second attempt of optimization for the model was to try to utilize the same model but with new activations for the two hidden layers.

<table>
<tr>
<th>Layer</th>
<th>Nodes</th>
<th>Activation</th>
</tr>
<tr>
<td>1</td>
<td>20</td>
<td>sigmoid</td>
</tr>
<tr>
<td>2</td>
<td>10</td>
<td>sigmoid</td>
</tr>
<tr>
<td>output</td>
<td></td>
<td>sigmoid</td>
</tr>
</table>

<img src="Resources/optimization3_setup.png">

After training this model by running it through 100 epochs, the model showed an accuracy of 72.03%. A small decrease in accuracy. This model is the least accurate model so far, and is obviously not the accuracy we need to utilize the model.

<img src="Resources/optimization3_results.png">


## Total Model Overhaul

We decided we need to try make some larger changes to see if we could raise the accuracy of our model. So we completely started over in the process. The first step to preparing the data is to read the data in from the CSV file we were provided, and get it loaded into a dataframe.

<img src="Resources/optimization4_data.png">

The next step is to start the cleansing by removing data columns which are not necessary or important to the analysis. In the case of this dataset we dropped four columns to make the dataset smaller and possibly less confusing to the model. We dropped
<ul>
<li> EIN - which is an identifier column</li>
<li> NAME - which are identifier column</li>
<li> INCOME AMT - Amount of income identified for the charity</li>
<li> USE_CASE - Use case identified for the grant</li>
</ul>

<img src="Resources/optimization4_data_cleaning.png">

The next step of the data prep is to encode the string data into usable values, 1 or 0.  The encoding process produces a dataset which looks like:

<img src="Resources/optimization4_data_encoding.png">

With the new dataset, we decided to try changing th model as well. This attempt of optimization for the model was to try to utilize a three layer model with a mix of activation types.

<table>
<tr>
<th>Layer</th>
<th>Nodes</th>
<th>Activation</th>
</tr>
<tr>
<td>1</td>
<td>20</td>
<td>relu</td>
</tr>
<tr>
<td>2</td>
<td>10</td>
<td>relu</td>
</tr>
<tr>
<td>3</td>
<td>5</td>
<td>sigmoid</td>
</tr>
<tr>
<td>output</td>
<td></td>
<td>sigmoid</td>
</tr>
</table>

<img src="Resources/optimization4_setup.png">

After training this model by running it through 100 epochs, the model showed an accuracy of 72.13%. A small decrease in accuracy. This model is nearly the least accurate model so far, and is obviously not the accuracy we need to utilize the model.

<img src="Resources/optimization4_results.png">


## Final Thoughts

After trying multiple iterations of different combinations of the following:
<ul>
<li>activation types</li>
<li>output types</li>
<li>number of nodes per layer</li>
<li>number of hidden layers</li>
</ul>

Our accuracy didn't change much it was always between 72.0% and roughly 73.2%. None of these models were up to the specified accuracy requested by Andy Glad the company president. We will have to provide him a report stating we couldn't get to the requested level and that the dataset does not seem to support the ability to differentiate  records enough to make an accurate model to the level of accuracy requested.    

