
<p align="center">
    <a href="https://acss-dig.psl.eu/"><img src="./files/logo_acss_psl.png" alt="logo" width="400" /></a>
</p>

<p align="center">
    <a href="https://acss-covid.vercel.app/">https://acss-covid.vercel.app</a>
</p>

# Covid19 politics / media twitter database

> This repository aims to make available the sources / programs needed to create the Covid19 politics / media twitter database.<br>
> It is a project supported by the Applied Computational Social Sciences Data-Intensive Governance - PSL Institute [https://acss-dig.psl.eu/](https://acss-dig.psl.eu/).

## Presentation slides
* [Covid19_slides_2022-01-24.pdf](./files/Covid19_slides_2022-01-24.pdf)

## Raw database with minimal cleaning (password protected)
* For Python users [pandas dataframe saved to a pickle object](https://universitedauphine-my.sharepoint.com/:u:/g/personal/bruno_chavesferreira_dauphine_psl_eu/Ef5MCyk5pghHhAm8PKh5wacBrJK-k0Zg6MqdAfnDvB4LFg?e=dDB5Sc)   
* For others (e.g. R users) [SqLite database](https://universitedauphine-my.sharepoint.com/:u:/g/personal/bruno_chavesferreira_dauphine_psl_eu/ESe4HtKVK9pOoUOuxtvvqM4B6H40GauZhyyQ5NZT2WQU9g?e=k4WvKS)

[Instructions for reading this data](#instructions).

## Descriptive statistics
* Accounts and tweets: [https://acss-covid.vercel.app/01_explore.html](https://acss-covid.vercel.app/01_explore.html)
* Trends: [https://acss-covid.vercel.app/02_trends.html](https://acss-covid.vercel.app/02_trends.html)
* Number of words : [https://acss-covid.vercel.app/03_nb_words.html](https://acss-covid.vercel.app/03_nb_words.html)
* Tweets distribution by account type / country: [https://acss-covid.vercel.app/05_account_type_distribution](https://acss-covid.vercel.app/03_nb_words.html)
* Politics repartition by categories (minister, ministry, party, party_leader): [politics_accounts.xlsx](./files/politics_accounts.xlsx)

## Other sources
* Parliaments’ compositions and the parties’ leaders: [POLITICS_abir.pdf](./files/POLITICS_abir.pdf)
* Matching with the parlgov database: [covid_twitter_politics_accounts_v4_Antoine.xlsx](./files/covid_twitter_politics_accounts_v4_Antoine.xlsx)
* The parlgov database: [https://www.parlgov.org/data-info/](https://www.parlgov.org/data-info/)

## <a name="instructions"></a>Instructions to read the data

### Python users to read the pickle file
```{python}
import pandas as pd
df = pd.read_pickle('file_name.pickle')
```

### R users: read the SqLite table
```{r}
install.packages("RSQLite")
library(DBI)

con <- dbConnect(drv=RSQLite::SQLite(), dbname="file_name.db") ## connect to the database
tables <- dbListTables(con) # you will see the table tweets

tweets_df <- dbGetQuery(conn=con, statement=paste("SELECT * FROM tweets", sep="")) # select the table tweets
```