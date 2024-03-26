![Image Alt Text](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/raw/main/cyber102/logo.JPG)

## Project Description
In this project I will be searching, analyzing, and visualizing data using Splunk. The project aims to provide hands-on experience with Splunk's capabilities, enhancing critical thinking and problem-solving skills through real-world data scenarios.

## Goals
- Apply Splunk search, analysis, and visualization techniques to solve real-world problems.
- Improve critical thinking and problem-solving skills.
- Gain experience with searching and analyzing data in a competitive environment.
- Develop a deeper understanding of Splunk's capabilities.

## 🤔 Reflection
If I had to explain "what is SIEM" in 3 emojis, they would be...
- 👀 - SIEM is always on the lookout at what is happening in the network.
- 🖥️ - It's that system that gathers information.
- 🛡️ - Helps in guarding systems against malicious actors.

## CTF Challenges

### Part 1 - Netflix Data Exploration: Uncover insights into TV shows and movies on Netflix, including genres, ratings, and release years.
 

index=main host=Netflix

👥 ***Challenge 1:** How many TV shows on Netflix are in the Docuseries genre?*

**Query:**
```spl
index=main host=Netflix type="TV Show" listed_in="Docuseries"
| stats count AS "Num_Tvshows_Docuseries"
```
**Result:**
```spl
| Num_Tvshows_Docuseries|
|-----------------------|
| 85                    |
```

👥 ***Challenge 2:** How many movies on Netflix have a rating of TV-PG?*

**Query:**
```spl
index=main host=Netflix type="Movie" rating="TV-PG" | stats count AS "Num_Movies-TV-PG"
```
**Result:**
```spl
| Num_Movies-TV-PG |
|------------------|
|        540       |
```
👥 ***Challenge 3:** How many movies on Netflix were released in the year 2020?*

**Query:**
```spl
index=main host=Netflix type="Movie" release_year="2020"
| stats count AS "2020_Releases"
```
**Result:**
```spl
| 2020_Releases |
|---------------|
|      517      |
```
👥 ***Challenge 4:** What is the longest duration by season on Netflix, and what is its TV rating?*

**Query:**
```spl
index=main host=Netflix type="TV Show" | stats max(duration) as max_duration by title, rating
| sort -max_duration | head 1
```
**Result:**
```spl
|         title         | rating | max_duration |
|-----------------------|--------|--------------|
|   Grey's Anatomy      | TV-14  |  17 Seasons  |
```
👥 ***Challenge 5:** How many movies on Netflix are listed as action and are rated PG-13?*

**Query:**
```spl
index=main host=Netflix type="Movie" listed_in="Action & Adventure" rating="PG-13"
| stats count AS "Num_Action_PG-13"
```
**Result:**
```spl
| Num_Action_PG-13 |
|------------------|
|        23        |
```
👥 ***Challenge 6:** How many movies and TV shows on Netflix have their country of origin as Turkey?*

**Query:**
```spl
index=main host=Netflix country="Turkey" | stats count AS "Origin-Turkey"
```
**Result:**
```spl
| Origin-Turkey |
|---------------|
|      105      |
````

👥 **Challenge 7:** Which release year had the most movies rated G? (Not TV-G)

**Query:**
```spl
index=main host=Netflix rating="G" | stats count by release_year | sort -count | head 1
```
**Result:**
```spl
| release_year |
|--------------|
|     2009     |
`````

👥 ***Challenge 8:** What two TV-Y7 rated shows were released in 2019 and were added to Netflix on November 22, 2019?*

**Query:**
```spl
index=main host=Netflix rating="TV-Y7" date_added="November 22, 2019" release_year=2019
| stats values(title) as TV_Y7_Shows
```
**Result:**
```spl
|           TV_Y7_Shows     |
|---------------------------|
| The Dragon Prince, Trolls |
|  The Beat Goes On!        |
```
👥 ***Challenge 9:** Which year had the most movies from the United States?*

**Query:**
```spl
index=main host=Netflix type="Movie" country="United States"
| stats count by release_year | sort -count | head 1
```
**Result:**
```spl
| release_year |
|--------------|
|     2017     |
```
👥 ***Challenge 10:** What is the oldest TV show by Release Year on Netflix?*

**Query:**
```spl
index=main host=Netflix type="TV Show" | stats min(release_year) as earliest_release_year by title
| sort earliest_release_year | head 1
```
**Result:**
```spl
|              title                |
|-----------------------------------|
| Pioneers: First Women Filmmakers* |
```
PathCode Inc. Breach Analysis: Analyze logs to detect the attacker's activities, including attempted logins and file uploads.
