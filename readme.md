# Insights into Starting Pitchers' Season Strikeout Numbers

Michael Scognamiglio & Jose Ramirez

Sources: PyBaseball, Baseball-Reference, FanGraphs


## Project Introduction

This project analyzes strikeout numbers for a starting pitcher in a season. For this analysis, we used a dataset of pitching statistics ranging from 2014 to 2019 on a season by season basis. Through exploratory data analysis and building an accurate interpretable linear regression model, the goal of this project is to gain insights into what statistics are most important in determining a starting pitcher's season strikeout numbers. As a result of our analysis and modeling, we are confident that we can provide a baseball general manager with a novel framework to capitalize on market inefficiencies in free agency. 

## Repository Structure

* pngs -- contains visualizations that highlight key features  in our analysis
* jupyter_notebooks -- contains the chronological breakdown of all the code used in our exploratory data analysis, statistical testing, model building, and post-model analysis. The order of the notebooks is 'Baseball_Refernce_Data_Collection','fangraphsdf_merging_with_briefdf','Mlb_Data_Cleaning_Stats_Analysis','Baseball_EDA_feature_elimination_stats','Modeling','Model_Predictions_Analysis', and then 'Post_Modeling_Analysis'.
* README.md
* presentatiion pdf -- contains pdf version of project presentation 

## Data 

For our project, we used a powerful baseball library contained in Python called PyBaseball. This library provided us with a vast array of pitching statistics from Baseball-Reference and FanGraphs. The Baseball-Reference dataset gave us more traditional baseball statistics while FanGraphs gave us the baseball statistics used in modern-day analytics. After merging these datasets, we filtered down the possible features for our model from over 330 features down to 34. 

## Statistical Tests

In an effort to engineer features for our model, we wanted to test a few hypotheses that we formed based on prior baseball knowledge and our EDA:

*  Do starting pitchers with elite fastball velocity garner more strikeouts in a season than pitchers with unremarkable fastball velocity?

	<img src="https://raw.githubusercontent.com/Sonora27/baseball-project/master/pngs/Strikeouts%20of%2095%20mph%2B%20Pitchers%20vs%20Soft%20Tossers.png">

	* From our two sample means test with a test statistic of 5.3, we were able to reject the null hypothesis that fastball velocity does not have an affect on starting pitcher season strikeouts. This finding allows us to conclude that starting pitchers with elite fastball velocity obtain better season strikeout numbers than those without elite fastball velocity. 


* Controlling for elite fastball velocity and pitchers with high endurance in a season, does a starting pitcher throwing his first pitch in an at-bat as a strike greatly influence his season strikeout total?

	* With a test statistic of -2.60 and a p-value of .002, we are able to conclude that a starting pitcher with a high first-strike percentage is far better able to garner strikeouts in a season than the population.

	

* Does a starting pitcher's best pitch have any demonstrable effect on their season strikeouts numbers?

	<img src="https://raw.githubusercontent.com/Sonora27/baseball-project/master/pngs/Average%20Strikeouts%20for%20a%20Starting%20Pitcher%20by%20Best%20Pitch.png">

	* From our ANOVA test with an F-statistic of 12.51, we were able to determine that a starting pitcher's best pitch does indeed have a significant impact on their season strikeout numbers.

* Does a starting pitcher's ability to induce swings on pitches from outside the strikezone significantly impact their strikeout numbers in a season?

	* With a test statistic of 8.30 and a p-value of approximately 0, we received a strongly singificant result that starting pitchers who get batters to swing outside of the strikezone at a high rate post higher season strikeout numbers.

## Modeling 

We sought to create a model to provide a baseball team's general manager with novel insights into which pitching statistics most accurately relate to their season strikeout totals. In order to accomplish this, we had to generate a model with a high level of accuracy. 

* To obtain a baseline of model performance, we first created a simple linear regression model with no additional feature elimination. For this model, we obtained a testing RMSE of 8.65 and a testing R Squared of .97.

	* Despite these strong findings, we decided to utilize feature elimantion due to the high dimensionality of our simple model.

* In order to resolve the high dimensionality of our initial model, we decided to use the Recursive Feature Elimination algorithm. This enabled us to downsize our feature list to 34. Using this algorithm, we obtained a testing RMSE of 8.78 and a testing R squared of .969. 

	* Even though these results were very slightly worse than simple mode, we preferred this model due to the fact that high dimensionality was no longer an issue for us.

* Another feature elimination method that we tried is Select K-best features.

	* From utilizing this method, we obtained a less satisfactory RMSE of 10.33. As a result, we preferred the model with Recursive Feature Elimination.

* In an effort to use a different model type, we also tried the Ridge model.

	* Our results from using this model type was an RMSE of 8.78 and an R sqaured of .972. This model performed simiarly to our initial two models. As a result, we finally decided on the model that used the Recursive Feature Elimination because it gave us the best balance of model performance and interpretability.

	<img src="https://raw.githubusercontent.com/Sonora27/baseball-project/master/pngs/Distrubution%20of%202019%20SP%20Strikeout%20Predictions.png">



## Modeling Conclusions



* Based on these metrics, we conclude that a general manager can feel confident that our model will give an accurate estimate of a pitcher's total strikeout numbers in a given year. Thus, we believe a lot of insight into strikeout numbers for starting pitchers can be found by analyzing our model.

* By analyzing our model's coefficients and our baseball knowledge, we conclude that a starting pitcher's previous season HR numbers and Hard Hit rate should not exclude a pitcher for being considered for a contract. The reason for this is becuase our model actually found a strong correlation between these features and our target variable (strikeouts). Despite the fact that our model found high coefficents for these features, through our hypothesis testing, we found that a pitcher who throws 95 mph or greater is far more likely to post high strikeouts numbers. Thus, we recommend that a general manager not outright dismiss a player who allows high HR numbers because that pitcher may have elite fastball velocity, which leads to high strikeout numbers.

	<img src="https://raw.githubusercontent.com/Sonora27/baseball-project/master/pngs/Impact%20of%20FB%20velo%20on%20SO%20for%20Homerprone%20Pitchers.png">

	* As can be seen in the figure above, a homer-prone starting pitcher with elite fastball velocity will still post significantly higher strikeout numbers in a season than a homer-prone starting pitcher who does not have elite fastball velocity.

* Based on our model's coefficents, we would also recommend that a GM prioritizes a pitcher's pitch efficiency over any other statistic. In our model, we found that the amount of balls a pitcher throws is mostly strongly correlated (in the negative direction) out of all our coefficients. Thus, we encourage GM's to look closely at starting pitchers who have most effectively minimized the amounts of balls thrown in a season. This allows for starting pitchers to provide more length in their starts as well as increase their strikeout numbers.
	<img src="https://raw.githubusercontent.com/Sonora27/baseball-project/master/pngs/Impact%20of%20Pitch%20efficency%20on%20SO%20for%20Starting%20Pitchers.png">

## Further Analysis

* Create a highly accurate interpretable model for relief pitchers. The purpose of this model would be to see if the insights obtained in our current model would hold for the relief pitching market as well.

* Create a general pitching predictive model for Earned Run Average. In this model we would also like to see if the insights we gained from our current model woud help the performance of the predictive model.















