
## CYB102 Project 5 Splunk
## Project Description
In this project I will be searching, analyzing, and visualizing data using Splunk. The project aims to provide hands-on experience with Splunk's capabilities, enhancing critical thinking and problem-solving skills through real-world data scenarios.

## Goals
- Apply Splunk search, analysis, and visualization techniques to solve real-world problems.
- Improve critical thinking and problem-solving skills.
- Gain experience with searching and analyzing data in a competitive environment.
- Develop a deeper understanding of Splunk's capabilities.

## 🤔 Reflection I
If I had to explain "what is SIEM" in 3 emojis, they would be...
- 👀 - SIEM is always on the lookout at what is happening in the network.
- 🖥️ - It's that system that gathers information.
- 🛡️ - Helps in guarding systems against malicious actors.
## 🧠 Reflection II
What field do you think is most important for logs to have?
- Timestamp - We want to know exactly when an event occurred. This can help in measuring the scope of the attack.

## CTF Challenges

Use the answer boxes below to document any CTF challenges you completed. If you don’t complete a particular challenge, leave it blank.

### Part 1 - Searching the Netflix Data (1pt each)

index=main host=Netflix

👥 Challenge 1: How many TV shows on Netflix are in the Docuseries genre?

**Query:**
```spl
index=main host=Netflix type="TV Show" listed_in="Docuseries" | stats count AS "Num_Tvshows_Docuseries"


