Yeh poora clean formatted **`README.md`** text hai. Aap simple neeche diye gaye box ke top-right se **Copy** button par click karke apni GitHub repository ki `README.md` file mein paste kar sakte hain:

```markdown
# SE-314: Software Construction — Lab 07
### 🧪 Test-First Programming II: Social Network Analysis

---

## 📌 Student & Course Information
* **Student Name:** Muhammad Zun U Rain Tahir
* **Course:** Software Construction (SE-314)
* **Class:** BESE-15AB
* **Institution:** National University of Sciences and Technology (NUST), SEECS
* **Instructor:** Dr. Sidra Sultana
* **Lab Engineer:** Mr. Aftab Farooq
* **Date:** October 23, 2026

---

## 🎯 Lab Objectives & CLOs
The primary goal of this lab is to build an analytical social network engine that infers follow-relationships from tweet `@mentions` and ranks top influencers by follower density, adhering to MIT 6.005 Problem Set 1 (Problem 3) specifications.

* **CLO-03:** Design and develop solutions based on Software Construction principles using test-first programming.
* **CLO-04:** Leverage modern software development toolchains including Eclipse IDE, JUnit 4, and Git/GitHub.

---

## 📁 Repository Structure

```text
ps1/
├── src/
│   └── twitter/
│       ├── Extract.java         # Tweet parsing and regex extraction
│       ├── SocialNetwork.java   # Graph inference & influencer logic
│       ├── Tweet.java           # Immutable Tweet class
│       ├── Timespan.java        # Timespan calculation
│       └── Main.java            # Main runner for live dataset
└── test/
    └── twitter/
        └── SocialNetworkTest.java # Comprehensive JUnit test suite

```

---

## 💡 Implementation Summary

### 1. Social Network Graph Inference (`guessFollowsGraph`)

* Scans tweet text for mentions using regex pattern: `(?<![A-Za-z0-9_-])@([A-Za-z0-9_-]+)`.
* Filters out self-mentions and ignores valid email patterns (e.g., `bitdiddle@mit.edu`).
* Normalizes all Twitter usernames to lowercase for case-insensitivity.
* Constructs a `Map<String, Set<String>>` mapping authors to sets of followed users.

### 2. Influencer Ranking (`influencers`)

* Calculates the number of followers (in-degree edges) for each user in the graph.
* Sorts users in strict descending order of follower count.
* Returns a `List<String>` of usernames ranked by influence.

---

## 🧪 Testing Strategy & Partitioning

A **Test-First (Red-to-Green)** workflow was strictly followed in `SocialNetworkTest.java`.

### Partition Space:

* **Number of Tweets:** `0`, `1`, `many`
* **Number of Mentions:** `0`, `1`, `many`
* **Author Case Sensitivity:** `lowercase`, `UPPERCASE`, `MixedCase`
* **Follower Distribution:** `0 followers`, `1 follower`, `many followers`, `tied influence`

### Key Test Cases Implemented:

1. `testGuessFollowsGraphEmpty` — Empty tweet list returns empty graph.
2. `testNoMentions` — Tweets with no `@mentions` yield no edges.
3. `testSingleMention` — Single mention correctly maps author $\rightarrow$ mentioned user.
4. `testMultipleMentions` — Author mapping to multiple mentioned users.
5. `testMultipleTweetsOneUser` — Multiple tweets from same user correctly merged.
6. `testCaseInsensitiveAuthor` — Case variations of author name resolved cleanly.
7. `testInfluencersEmpty` — Empty graph returns empty list.
8. `testSingleUserNoFollowers` — User without followers excluded/handled gracefully.
9. `testSingleInfluencer` — Correctly ranks single influencer.
10. `testMultipleInfluencersOrder` — Descending order by follower count.
11. `testTiedInfluence` — Equal follower counts handled without errors.

---

## 🖥 Output Verification

### JUnit 4 Test Results

```text
-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running twitter.SocialNetworkTest
Tests run: 11, Failures: 0, Errors: 0, Time elapsed: 0.053 sec

Result: PASSED (All 11 tests green)
-------------------------------------------------------

```

### Main Application Output (`Main.java`)

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

```

```
