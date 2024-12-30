---
NCIP: 24
Title: Arena Improvements
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com>, jeahyun choi <jonny@planetariumhq.com>, jiwon <jiwon@planetariumhq.com>
Created: 2024-12-30
---


## Abstract

The Arena feature is transitioning detailed rule processing to external services to reduce on-chain load and improve nuanced rules, aiming for a better gaming experience. 
Key updates include changes to ranking and scoring calculations, opponent list refresh methods, and clan score processing.

## Motivation

1. **Reduce timing sensitivity in Arena rules**:
    - Improve user experience by addressing high timing sensitivity, especially noted during the service disruption on Thor Planet on December 18, 2024.
2. **Expand operational flexibility**:
    - Create an environment where entities beyond Planetarium can manage Arena events.
3. **Reduce player fatigue**:
    - Simplify decision-making by reducing the need to check extensive opponent lists before playing.

## Rational

1. Offloading detailed rule processing to external services reduces chain load, enabling more intricate handling.
2. Create rule structures that accommodate players from various time zones.
3. Enable customizable rules (e.g., scoring and ranking methods) for different event organizers.
4. Enhance player experience by providing tailored opponent lists based on player’s level.

## Specification

### **Arena Rule Changes**

- **Ticket Refill Count**:
    - Initial and subsequent refills grant **5 tickets**.
    - A total of **20 refill stages** provides up to **100 tickets** as before.
    - Additional ticket purchases limited to **40 tickets** (4 per interval).
    - **Purchase Prices**:
        - Season: Starts at 1, increases by 0.2 per purchase.
        - Championship: Starts at 2, increases by 0.2 per purchase.
- **Score and Ranking Updates**:
    - **Current**: Score and rank updated after each battle.
    - **Revised**:
        - Updates occur at the start of each ticket refill interval.
        - Scores and win/loss stats for battles within an interval are displayed in the UI and reset at the next interval.
- **Opponent List Updates**:
    - **Current**: Opponents are displayed within a range of **+200 to -100 points** of the player’s score.
    - **Revised**:
        - At each ticket refill interval, 5 fixed opponents are displayed based on rank groups:
            - **Groups**: 2 groups above, 1 group at the same rank, and 2 groups below.
            - Opponents are chosen randomly from these groups.
            - Opponent refresh:
                - First refresh per interval is free.
                - Subsequent refresh costs: 10K crystals (second refresh), 1 NCG (for further refreshes).
        - **Scoring Table**:
            
            
            | Group | Range (%) | Win Score | Loss Score |
            | --- | --- | --- | --- |
            | Upper 1 | 20–40% above | +24 | -1 |
            | Upper 2 | 40–80% above | +22 | -2 |
            | Same | 80–120% equal | +20 | -3 |
            | Lower 1 | 120–180% below | +18 | -4 |
            | Lower 2 | 180–300% below | +16 | -5 |
        - If fewer than 5 opponents are available in groups, additional opponents are selected from lower groups.
        - **Example**: Rank 1 player’s list includes 2 from the same group and 3 from the group below.
    - Battles cost **5 AP per action**.
    - Ingredients previously awarded as Arena rewards are now obtainable from specific stages in each world.

---

### **Battle and Score Processing Updates**

- **Opponent List & Scoring**:
    - Transferred from on-chain contracts to dedicated external services.
- **Event Management**:
    - Allows event organizers other than Planetarium to customize rules (e.g., scoring and ranking).
- **On-Chain Records**:
    - Chain will log and return battle results processed through external services.

---

### **Clan Battle Feature**

- **Clan Scoring**:
    - Clan scores are calculated by summing the top 10 players’ scores within the clan.
- **Rewards**:
    - Clan rankings determine rewards at the end of the season.
- **Details**:
    - Refer to the dedicated NCIP for clan-related updates.

---

### **Expected Schedule**

- Initially planned for Thor Planet in **200270**, but due to the complexity of transitioning rule handling to external services, it will be implemented in **200280**.
- **200280 Adjustments**:
    - Simultaneous Arena updates across all chains.
    - Thor-specific temporary clan rankings and aggregation for final testing before full deployment.
1. **Early February 2025**: Previewnet setup and feedback collection.
2. **Mid-February 2025**: Mainnet release with version 200280:
    - Ticket refill timing updates.
        - Display 5 opponents based on rank groups.
        - Additional opponent refresh options.
    - Clan ranking and list display.
        - Additional rankings and rewards for top clan members (Thor-only).



