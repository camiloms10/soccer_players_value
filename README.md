<div id="top"></div>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/camiloms10/soccer_players_value">
    <img src="images/transfermarkt.png" alt="Logo" width="300" height="80">
  </a>

<h3 align="center">Soccer Players Value Prediction Model</h3>

  <p align="center">
    This project was made using Python, specifically Pandas and ScikitLearn, to analyze the top Soccer Players market value after the 2021/2020 season, and generating a prediction model to for this value.
    <br />
    <a href="https://github.com/camiloms10/soccer_players_value"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/camiloms10/soccer_players_value/issues">Report Bug</a>
    ·
    <a href="https://github.com/camiloms10/soccer_players_value/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#data-sources">Data Sources</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <!--<li><a href="#contributing">Contributing</a></li>-->
    <!--<li><a href="#license">License</a></li>-->
    <li><a href="#contact">Contact</a></li>
    <!--<li><a href="#acknowledgments">Acknowledgments</a></li>-->
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

<img src="images/FIFA.png" alt="Logo" width="200" height="100">

Through this project you´ll find multiple prediction models. such as multiple linear regression and random forest, in order to find best fit between the independent variables (player statistics through the season) and the dependent variable (Value).
<p align="right">(<a href="#top">back to top</a>)</p>



### Built With

* [Python](https://www.python.org)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started


### Prerequisites

These are the python libraries you´ll need to run the ipynb file.
* Libraries
  ```sh
  pip install numpy
  pip install seaborn 
  pip install matplotlib
  pip install pandas
  pip install sklearn 
  pip install scipy
   ```

<p align="right">(<a href="#top">back to top</a>)</p>

### Data Sources

The data source of this project where downloaded from [Kaggle](https://www.kaggle.com/sanjitva/predicting-soccer-player-transfer-values)
* These are the csv files used inside the project

  * **players_stats_value.xlsx :** Top 2500 players based on market value and their 2021-2017 statistics (goals, assists, passes leading to goals, crosses, tackles, etc.)

<p align="right">(<a href="#top">back to top</a>)</p>




<!-- USAGE EXAMPLES -->
## Usage

You can use this data to analyze:
* How a player has performed through time
* The correlation between individual statistics and player value
* Predict player´s value based on individual statistics (this is what we´ll focus on)
* Etc.
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

To do ALL of the following analysis first I did the import via pd.read_excel commands and changed the dataframes as I needed to, you can check that inside the [.ipynb file](players_value.ipynb) with the step by step solution.

**I used the 90% of the dataframes to train the models and the remaining 10% to test the model.**

### 1. Regression and Random Forest (using most correlated 2021/2020 season stats vs. player Value)

<p align ="center">

|                                                | Value               |
|------------------------------------------------|---------------------|
| Value                                          | 1.0                 |
| Goal Creating Actions (20/21)                  | 0.5182500696903144  |
| Total Carries in Forward Direction (20/21)     | 0.5129803351797286  |
| Number of Times Player was Pass Target (20/21) | 0.5118986575690919  |
| Passes Leading to Goals (20/21)                | 0.5096111547070523  |
| Non-penalty xG+ xA (20/21)                     | 0.5083183735823256  |
| Passes Leading to Shot Attempt (20/21)         | 0.5031947476181425  |
| Touches in Attacking Penalty Box (20/21)       | 0.49484671236655164 |



* I got 7 results >= .49 correlation between them and value
* We got a .36 score for our linear regression model considering the top 7 variables correlated to Value, as this score is still low we´re going to try other approaches to increase it.
  
<p align ="center">
<img src="images/top7_correlation_model_error_distribution.png" width="400" height="300">

</p>
* Then I tried using the Random Forest prediticon model using those same indepentent variables we used in the regression model and increased the score from .36... to approximately .38.

</p>



### 2. Standardizing my dataframe using ScikitLearn StandardScaler

<p align ="center">

|   | Value             | Goal Creating Actions (20/21) | Total Carries in Forward Direction (20/21) | Number of Times Player was Pass Target (20/21) | Passes Leading to Goals (20/21) | Non-penalty xG+ xA (20/21) | Passes Leading to Shot Attempt (20/21) | Touches in Attacking Penalty Box (20/21) |
|---|-------------------|-------------------------------|--------------------------------------------|------------------------------------------------|---------------------------------|----------------------------|----------------------------------------|------------------------------------------|
| 0 | 8.83416419601431  | 5.2149035180193435            | 3.0888723567336447                         | 1.5853588482790255                             | 3.2291146602806995              | 4.9325641354366105         | 2.2281528228750886                     | 5.459029630475353                        |
| 1 | 7.031431813358088 | 2.6141465522461735            | 0.11944508802251795                        | 0.5744640680313485                             | 2.292357521590521               | 5.2136219209315735         | 0.7790340910270162                     | 3.4721126362883212                       |
| 2 | 6.430521019139348 | 4.564714276576051             | 1.2778480335087268                         | 1.8694281179222683                             | 3.8536194194074853              | 4.955985617561191          | 2.2764567806033575                     | 2.92399760340914                         |
| 3 | 5.228699430701866 | 3.9145250351327587            | 2.7299305989773544                         | 1.736209425951644                              | 4.478124178534271               | 2.2859366553590377         | 3.0976240619839315                     | 2.193177559570232                        |
| 4 | 5.228699430701866 | 2.1806870579506454            | 2.3873043756645322                         | 2.6060491205833665                             | 2.292357521590521               | 4.440713010820425          | 3.0976240619839315                     | 6.281202179794125                        |
</p>



* The regression using the standardized dataframe didn´t have the effect we were looking for, as it gave us the same .36 we had with the initial dataframes.

</p>

<p align ="center">
<img src="images/standardized_dataframe_error_distribution.png" width="400" height="300">
<p align ="center">
We´re limiting this histogram from -100% error to 100% error to appreciate the predictions better in this range, but we got outliers out of this limits.
</p>
</p>


### 3. Using all of 2021-2020 cuantitative statistics

<p align ="center">
<img src="images/quantitative_stats_model_error.png" width="400" height="300">
<p align ="center">
We can see how the distribution is more centralized (between -1,1) vs. the previous prediction models.
</p>
</p>

* **We went from having previous predictive scores between .36-.38 to a .59 score** this means our model can predict correctly 59% of the tests we do, that´s a huge improvement using all the cuantitative variables from the 2021/2020 season instead of the most correlated (>.5)
* 2 pointer shots percentage made has increased from 2013 till 2019 (48% to 52%), meanwhile 3 pointers remain at the 36% range

### 4. Variables significance (p-value)
<p align ="center">
<img src="images/significant_variables_error_distributions.png" width="400" height="300">
<p align ="center">
We can see a similar distribution between #3 and #4 as they have a close scores .59 and .56
</p>
</p>

* Now I´ll generate a last regression model, this will be based on getting the variables with demonstrated significance in the model (this means that they actually affect 'Value'), all of this calculations will be generated using scipy and the pearson correlation p-value
* Using only the significant variables in our model we also got a much higher score from our initial 2 models (correlation based), **increased from .36-38 to .56**, this means our model can predict %56 correctly
* Comparing the predictions vs the real values in our test dataframe,  we can see how we got both positive and negative outliers with -5600% error and +300% error, but we also have some predictions that are close to the real value (tending to 0% error)

## Final Conclusions

- While using regression predictive models we should focus on those independent variables that are significantly related to the dependent variable as it gave us a much higher regression score (59%).
- Generating the standardization of the data didn´t have the effect we were hoping, this means the scales between the columns weren´t that much different, but this tool could help us in other project.

See the [open issues](https://github.com/camiloms10/soccer_players_value/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING 
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>
-->


<!-- LICENSE 
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>
-->


<!-- CONTACT -->
## Contact

Camilo Manzur - [@LinkedIn](https://www.linkedin.com/in/camilo-manzur-4b7137a8/)

Project Link: [https://github.com/camiloms10/soccer_players_value/](https://github.com/camiloms10/soccer_players_value/NBA_project)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS 
## Acknowledgments

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>
-->


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/camiloms10/soccer_players_value.svg?style=for-the-badge
[contributors-url]: https://github.com/camiloms10/soccer_players_value/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/camiloms10/soccer_players_value.svg?style=for-the-badge
[forks-url]: https://github.com/camiloms10/soccer_players_value/network/members
[stars-shield]: https://img.shields.io/github/stars/camiloms10/soccer_players_value.svg?style=for-the-badge
[stars-url]: https://github.com/camiloms10/soccer_players_value/stargazers
[issues-shield]: https://img.shields.io/github/issues/camiloms10/soccer_players_value.svg?style=for-the-badge
[issues-url]: https://github.com/camiloms10/soccer_players_value/issues
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/camilo-manzur-4b7137a8/
[product-screenshot]: images/screenshot.png