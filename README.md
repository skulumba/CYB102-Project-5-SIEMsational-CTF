![Image Alt Text](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/raw/main/cyber102/logo.JPG)

## Project Description
Splunk  In this project I will be searching, and analyzing log data using Splunk. This project aims to demonstrate the power and versatility of Splunk in aggregating, searching, and analyzing log data from various sources!

## Technologies Used:
- Splunk Enterprise
- Splunk Search Processing Language (SPL)
  
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

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/342a248e-ceb4-4d84-aee9-8274f7981428)

**Result:** 

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/4fc2e9f0-2dce-47c1-b653-8f59d131592d)



👥 ***Challenge 2:** How many movies on Netflix have a rating of TV-PG?*

**Query:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/4ad37fd4-28a7-41e0-84cb-3ecd2712cf03)

**Result:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/2015fd3f-4cbb-445e-8005-45ae41e88a79)

👥 ***Challenge 3:** How many movies on Netflix were released in the year 2020?*

**Query:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/3ea1720f-1c27-44c8-8cc9-d81ebf7cbd91)

**Result:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/b62ca856-e9b0-444d-ab1c-2c81dcbc39ee)


👥 ***Challenge 4:** What is the longest duration by season on Netflix, and what is its TV rating?*

**Query:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/5113273c-fa6b-4da2-8b32-8df9fc4233f2)

**Result:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/0900272e-5f2b-468a-9724-e0befcf1b54a)


👥 ***Challenge 5:** How many movies on Netflix are listed as action and are rated PG-13?*

**Query:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/84b007cd-7ce7-419e-947e-defafadc2f03)

**Result:**

![image](https://github.com/skulumba/CYB102-Project-5-SIEMsational-CTF/assets/75015106/ff8b7e7d-ec45-45b6-9a25-cd5a92d236c5)

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
