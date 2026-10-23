Here is a complete, professionally styled `README.md` file tailored specifically to your GitHub repository and lab requirements. You can copy and paste this directly into your `README.md` file on GitHub!

---

```markdown
# SE-314: Software Construction — Lab 07
> **Test-First Programming II: Social Network Analysis**  
> **Course:** Software Construction (SE-314) | **Class:** BESE-15AB  
> **Institution:** National University of Sciences and Technology (NUST), SEECS  
> **Date:** October 23, 2026  

---

## 👨‍💻 Student Details
* **Author:** Muhammad Zun U Rain Tahir
* **Instructor:** Dr. Sidra Sultana
* **Lab Engineer:** Mr. Aftab Farooq

---

## 📌 Overview & Objectives
This repository contains the implementation and test-first engineering workflow for **Lab 07 (MIT 6.005 Problem Set 1: Tweet Tweet — Problem 3)**. 

The goal of this project is to build an analytical social network toolbox that infers user follow-relationships based on evidence extracted from Twitter data (`@mentions`) and ranks top influencers by follower density.

### Key Learning Outcomes (CLOs):
* **CLO-03:** Design and develop software solutions adhering to core software construction and test-first programming principles.
* **CLO-04:** Leverage modern software engineering toolchains including **Eclipse IDE**, **JUnit 4 testing framework**, and **Git/GitHub** version control.

---

## 🛠 Project Architecture & Components


```

ps1/
├── src/
│   └── twitter/
│       ├── Extract.java         # Text parsing & regex mention extraction engine
│       ├── SocialNetwork.java   # Graph inference & influencer ranking logic
│       ├── Tweet.java           # Immutable Tweet data model
│       ├── Timespan.java        # Time range representation
│       └── Main.java            # Execution entry point for live dataset analysis
└── test/
└── twitter/
└── SocialNetworkTest.java # JUnit test suite covering partition domain spaces

```

---

## 🔬 Core Implementation Details

### 1. Inferring the Social Network (`guessFollowsGraph`)
* Parses raw tweet data to extract user mentions using a robust regular expression: `(?<![A-Za-z0-9_-])@([A-Za-z0-9_-]+)`.
* Ignores email addresses (e.g., `user@domain.com`) to prevent false-positive follow edges.
* Normalizes all Twitter usernames to **lowercase** to ensure case-insensitive parity.
* Constructs an adjacency list graph represented as `Map<String, Set<String>>`.

### 2. Influencer Ranking (`influencers`)
* Aggregates follower counts across all follow lists in the graph.
* Computes influence score per user based on unique incoming edges.
* Returns a sorted list (`List<String>`) of distinct usernames in descending order of influence.

---

## 🧪 Testing Strategy (Partition-Based Approach)

Unit testing followed a strict **Test-First (Red-to-Green)** paradigm, ensuring specifications were validated prior to implementation.


```

Input / Output Domain Partitions:
├── Number of tweets: [0, 1, many]
├── Number of @mentions: [0, 1, many]
├── Author case sensitivity: [lower, UPPER, Mixed]
└── Follower count distribution: [0, 1, many, tied]

```

### Verified Test Cases (`SocialNetworkTest.java`):
1. **`testGuessFollowsGraphEmpty`**: Verifies empty tweet lists yield an empty graph.
2. **`testNoMentions`**: Ensures tweets without mentions create no outgoing edges.
3. **`testSingleMention`**: Validates correct edge creation for a single `@mention`.
4. **`testMultipleMentions`**: Verifies mapping multiple mentioned users to one author.
5. **`testMultipleTweetsOneUser`**: Confirms cumulative mention extraction across multiple tweets.
6. **`testCaseInsensitiveAuthor`**: Validates case-normalization for authors and mentions.
7. **`testInfluencersEmpty`**: Ensures empty network graphs yield empty influencer lists.
8. **`testSingleUserNoFollowers`**: Confirms users with zero followers are excluded/handled gracefully.
9. **`testSingleInfluencer`**: Verifies correct output for single-node influence.
10. **`testMultipleInfluencersOrder`**: Verifies strict descending sort order by follower density.
11. **`testTiedInfluence`**: Guarantees graceful handling when multiple users share equal influence.

---

## 🚀 Execution & Verification Results

### 1. JUnit Test Suite Execution (100% Green Bar)
All 11 unit test cases pass cleanly without errors or failures:


```

---

## T E S T S

Running twitter.SocialNetworkTest
Tests run: 11, Failures: 0, Errors: 0, Time elapsed: 0.053 sec

## SUCCESS: All tests passed! [====== GREEN BAR ======]

```

### 2. Live Dataset Execution Output (`Main.java`)
Running `Main.java` parses live sample tweet datasets and displays top network influencers:

```text
Fetched 10 tweets
ranging from 2026-10-23T10:00:00Z to 2026-10-23T10:00:00Z
covers 5 Twitter users
follows graph has 8 nodes
bob
carol
frank
alice
dave

```

---

## 🛠 Environment & Tools

* **Language:** Java 17 / OpenJDK
* **IDE:** Eclipse IDE 2026-12
* **Testing:** JUnit 4 / Hamcrest
* **Version Control:** Git & GitHub

---

## 📜 Copyright & Acknowledgments

Starter code provided by **MIT OpenCourseWare (6.005 Software Construction, Spring 2016)**.

Lab assignment designed for the **Department of Software Engineering, NUST SEECS**.

```

```
