# Load cleaned data

### Answers

**A: 1** Your answer here

Write a summary of the exploratory data analysis above. 
```
This EDA focuses primarilty on differences between resorts at the state level.
We first summarize all features at the state level

We calculate some ratios for Reports vs. Population and Area.
    Montana has many resorts per capita, but is 24th in resorts per square mile
    Montana is a large area (top 3rd) but relatively sparsely populated (top 24th) state
    
We then scale the state data and perform principal component analysis to get the maximum variance accross features.

We then concatenate out PCA information with Adult Weekend pricing raw data and quartiles 
    - We fill missing pricing data with the mean()
    - We fill missing quartile data with 'NA'
```

What numerical or categorical features were in the data?
```
- We summarized all numeric features by state
- We added numeric PCA calculations
- We merged numeric Adult Weekend pricing data by state
- We calculated categorical quartile information for Adult Weekend pricing by state
- We then looked at all correlations using  heatmap
- We zero'ed in on scatter plotting how pricing correlates with:
    'total_chairs_runs_ratio', 
    'total_chairs_skiable_ratio', 
    'fastQuads_runs_ratio', 
    'fastQuads_skiable_ratio'

```

Was there any pattern suggested of a relationship between state and ticket price? 
```angular2html

There are some stronger correlations with pricing, especially between pricing and
    - fastQuads
    - total chairs, 
    - skiable are and 
    - number of runs

but  it's too early to tell whether they are significant or to assume any actionable correlation or rationale.

```

What did this lead us to decide regarding which features to use in subsequent modeling? 
```angular2html

We can see some correlations, but can't yet tell why they exist. marketing factors, such as exclusivity (If there are fewer resorts can they charge a higher price?)
We still do not know for sure whether getting customer to runs faster can support higher pricing, but it's something to look at further.

```
What aspects of the data (e.g. relationships between features) should you remain wary of when you come to perform feature selection for modeling? 
```angular2html
Some of the data we are finding correlations - such as fastQuads may be misleading because during data-cleaning we were not sure how good ur data was.

```

Two key points that must be addressed are the choice of target feature for your modelling and how, if at all, you're going to handle the states labels in the data.
```angular2html
We can look ahead and see which features that the part 04 and 05 notebooks isolate for features, but in a real world, and with my limited experience I hesitate to think that summarizing by state alone would provide a complete picture.   
While resorts across the US segmented by state provides some interesting correlations with price, 
we have not really proved that the best way to segment is on state.  There could be larger or smaller geographic factors at play.  There could be better or worse marketing approaches, or some resorts may have for effective branding and can therefore command higher prices.  Differences in lodging, luxuries, and travel cost could also play a factor.  We don't have information about how many customers are 'locals' and how many travel to get to the resort, either by air-travel or shuttle.



```





### Summaries
    Largest states by area states are (Montana #3)
        Alaska        665384
        California    163695
        Montana       147040
        New Mexico    121590
        Arizona       113990

    Top population
            California      39512223
            New York        19453561
            Pennsylvania    12801989
            Illinois        12671821
            Ohio            11689100
            ...
            Montana comes in at 30th

    Resorts per state
        New York,33
        Michigan,28
        Colorado,22
        California,21
        Pennsylvania,19
        New Hampshire,16
        Vermont,15
        Wisconsin,15
        Minnesota,14
        Utah,13
        Idaho,12
        Montana,12  Montana and Utah are top 12th with 12 resorts



    Skiable area by state
        Colorado      43682.0
        Utah          30508.0
        California    25948.0
        Montana       21410.0   x
        Idaho         16396.0


    Total night Ski
        New York,2836.0
        Washington,1997.0
        Michigan,1946.0
        Pennsylvania,1528.0
        Oregon,1127.0
        Wisconsin,1065.0
        Minnesota,1020.0
        Montana,710.0     8th with

    Days open
        Colorado,3258.0
        California,2738.0
        Michigan,2389.0
        New York,2384.0
        New Hampshire,1847.0
        Vermont,1777.0
        Utah,1544.0
        Wisconsin,1519.0
        Minnesota,1490.0
        Pennsylvania,1404.0
        Oregon,1180.0
        Idaho,1136.0
        Washington,1022.0
        New Mexico,966.0
        Montana,951.0    Days open in entire state -- DIVIDE BY number of resorts

## Ratios - Pairs
    Resorts / Population   -- most action in the 1 resort per 1 - 50K or less population
    Resorts / Area         -- most action in the 1 resort per every 1-25 square miles with a long tail 

## Density
    Montana has many resorts per capita, but is 24th in resorts per square mile
    Montana is a large (3rd) but relatively sparsely populated (24th) state
    
## Scale the data (sklearn.scale() on the state_summary_scale dataset)
    Perentages of whole on the column feature)
    LOOK AT MEAN AND STD OF THE SCALED DATA
  

## Principal Component Analysis - Look at variance in on the state_summary_scale using PCA()
    - state_pca = PCA - identifying the main axes of variance within a data
    - PLOT state_pca.explained_variance_ratio_.cumsum()
    - concatenate PCA1,2 and Adult Weekend pricing
    - Add quartiles of Weekend Price
    - Fill missing pricing data with the mean()
    - FIll missing quartile data with 'NA'
 
## Correlations
- heatmap:  Turning your attention to your target feature, AdultWeekend ticket price, you see quite a few reasonable correlations. fastQuads stands out, along with Runs and Snow Making_ac. The last one is interesting. Visitors would seem to value more guaranteed snow, which would cost in terms of snow making equipment, which would drive prices and costs up. Of the new features, resort_night_skiing_state_ratio seems the most correlated with ticket price. If this is true, then perhaps seizing a greater share of night skiing capacity is positive for the price a resort can charge.
As well as Runs, total_chairs is quite well correlated with ticket price. This is plausible; the more runs you have, the more chairs you’d need to ferry people to them! Interestingly, they may count for more than the total skiable terrain area. For sure, the total skiable terrain area is not as useful as the area with snow making. People seem to put more value in guaranteed snow cover rather than more variable terrain area.
The vertical drop seems to be a selling point that raises ticket prices as well.
- Scatter ploting pricing gainst all

-Zero in- scatterploting Pricing against 
    'total_chairs_runs_ratio', 
    'total_chairs_skiable_ratio', 
    'fastQuads_runs_ratio', 
    'fastQuads_skiable_ratio'


