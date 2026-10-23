
```markdown
# 🧪 SE-314: Software Construction — Lab 07
> **Test-First Programming II: Social Network Analysis**

![Java](https://img.shields.io/badge/Java-17-orange.svg)
![JUnit](https://img.shields.io/badge/JUnit-4.13-green.svg)
![Build](https://img.shields.io/badge/Build-Passing-brightgreen.svg)
![License](https://img.shields.io/badge/MIT-6.005-blue.svg)

---

## 📌 Student & Course Overview

* **👨‍💻 Author:** Muhammad Zun U Rain Tahir
* **🏫 Institution:** National University of Sciences and Technology (NUST), SEECS
* **📚 Course:** Software Construction (SE-314) | **Class:** BESE-15AB
* **👩‍🏫 Instructor:** Dr. Sidra Sultana
* **👨‍🔧 Lab Engineer:** Mr. Aftab Farooq
* **📅 Date:** October 23, 2026

---

## 🎯 Objectives & Learning Outcomes

This lab focuses on implementing **Problem 3 (Social Network Analysis)** from the MIT 6.005 Problem Set 1 specifications using a **Test-First (Red-to-Green)** software engineering methodology.

* **CLO-03:** Design and develop software solutions adhering to core software construction and test-first development principles.
* **CLO-04:** Utilize modern development tools including **Eclipse IDE**, **JUnit 4 framework**, and **Git/GitHub** version control.

---

## 📁 Repository Structure

```text
ps1/
├── 📂 src/twitter/
│   ├── 📄 Extract.java         # Text parsing & regex mention extraction engine
│   ├── 📄 SocialNetwork.java   # Graph inference & influencer ranking logic
│   ├── 📄 Tweet.java           # Immutable Tweet data model
│   ├── 📄 Timespan.java        # Timespan calculation module
│   └── 📄 Main.java            # Main runner analyzing sample tweet datasets
└── 📂 test/twitter/
    └── 📄 SocialNetworkTest.java # JUnit test suite covering all input/output partitions

```

---

## 💡 System Architecture & Implementation

### 1️⃣ Social Network Graph Inference (`guessFollowsGraph`)

* Scans tweet text for mentions using a lookbehind regex pattern: `(?<![A-Za-z0-9_-])@([A-Za-z0-9_-]+)`.
* Ignores email formats (e.g., `user@domain.com`) and self-mentions.
* Normalizes all usernames to **lowercase** for complete case-insensitivity.
* Constructs a `Map<String, Set<String>>` representing directed follow edges.

### 2️⃣ Influencer Density Ranking (`influencers`)

* Calculates in-degree edge counts (total unique followers) for every user in the network graph.
* Sorts users in strict **descending order** based on total followers.
* Returns a `List<String>` of usernames sorted by influence level.

---

## 🧪 Testing Strategy (Partitioning Approach)

A strict **Red-to-Green Test-Driven Development (TDD)** workflow was implemented in `SocialNetworkTest.java`.

### 🔍 Domain Partitions Tested:

* **Tweet Count:** `0`, `1`, `many`
* **Mention Count:** `0`, `1`, `many`
* **Author Case Variants:** `lowercase`, `UPPERCASE`, `MixedCase`
* **Follower Distribution:** `0 followers`, `1 follower`, `many followers`, `tied rank`

### ✅ Test Suite Breakdown:

1. `testGuessFollowsGraphEmpty` — Verifies empty input returns an empty graph.
2. `testNoMentions` — Ensures tweets without `@mentions` produce no graph edges.
3. `testSingleMention` — Tests correct directed edge creation (author $\rightarrow$ mentioned user).
4. `testMultipleMentions` — Verifies mapping an author to multiple mentioned users.
5. `testMultipleTweetsOneUser` — Confirms mentions across multiple tweets are aggregated.
6. `testCaseInsensitiveAuthor` — Validates case normalization across author names.
7. `testInfluencersEmpty` — Confirms empty graph returns an empty influencer list.
8. `testSingleUserNoFollowers` — Ensures users without followers are safely handled.
9. `testSingleInfluencer` — Verifies ranking logic for single-influencer networks.
10. `testMultipleInfluencersOrder` — Confirms strict descending sort order by follower count.
11. `testTiedInfluence` — Handles tied follower counts smoothly without throwing exceptions.

---

## 🖥 Output & Verification

### 🟢 JUnit 4 Test Suite Results

```text
-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running twitter.SocialNetworkTest
Tests run: 11, Failures: 0, Errors: 0, Time elapsed: 0.053 sec

RESULT: PASSED (11/11 tests green)
-------------------------------------------------------

```

### 📊 Live Sample Execution Output (`Main.java`)

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

## 📜 Copyright & Acknowledgments

Starter codebase provided by **MIT OpenCourseWare (6.005 Software Construction)**.

Lab assignment executed for the **Department of Software Engineering, NUST SEECS**.

```

```
