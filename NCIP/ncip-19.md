---
NCIP: 19
Title: Guild System
Status: Draft
Type: Core
Author: Suho Lee <suho@planetariumhq.com.>.
Created: 2024-08-02
---

# Abstract

Despite NCIP-15 reducing network abuse, Mead remains easily accessible, necessitating a model requiring user contribution to the network. The proposed solution involves guilds paying Mead on behalf of players for transactions, maintaining a free-to-play (F2P) experience. Guilds gain influence through player staking, participating in network consensus, and earning NCG from player activities. A phased implementation begins with a Planetarium-only guild, expanding to third-party guilds, allowing broader participation and sustainable Mead provision without sole reliance on Planetarium.

# Motivation

## Preventing Abuse

Although the introduction of NCIP-15 prevented abusers who had a large negative impact on the network, it is still not in line with the purpose of introducing Mead, as users can still use Mead without a large burden.

Because of this, we need a way to require a certain amount of contribution to the network in order for users to use Mead. I think the easiest way is to pay the Gas fee, which is a common blockchain game method, to make people buy Mead. Nine Chronicles has been a F2P game for a long time, and changing that is not an easy decision.

So while regular players can still enjoy the game as F2P, we needed to find a way for them to contribute to the network just by playing.

## For Planetarium dependent network

With the introduction of NCIP-15, the game became unplayable without Mead. Mead is currently exclusively provided by Planetarium, which has led to Nine Chronicles being heavily dependent on Planetarium.

To solve this problem, it became necessary for other Nine Chronicles contributors other than Planetarium to provide Mead. However, in order to provide Mead while maintaining F2P, Nine Chronicles contributors would have to provide Mead for free like Planetarium, which we think is an unsustainable model.

# Rationale

## Guild

We designed the Guild unique to Nine Chronicles. In general games, guilds are used to provide a community space and a sense of belonging for users. However, the Guild in Nine Chronicles will have a slightly stronger meaning.

## Mead provide

Guilds are required to pay Mead on behalf of players belonging to the Guild for transactions made by them. This is similar to what the existing Planetarium provided under the name of Pledge, and players can continue to enjoy the same F2P experience as before by joining a Guild.

## Staking (Monster Collection)

Players can contribute to the Guild through Staking. Power staked through Monster Collection is delegated to the Guild, and the Guild can participate in network consensus through this delegated Power. 

Therefore, the Guild that gathers more players will receive stronger influence and network contribution rewards in the network, which becomes a motivation for the Guild to gather players even by supplying Mead.

### Unstaking

Players can request unstaking for their staked assets at any time. However, a minimum lockup period of 2 weeks is required, and during this period, they cannot exercise any rights to the assets they unstake.

Unstaking does not have to be done for all of the assets they staked at once. (e.g., 100NCG Stake, 50NCG Unstake)

### Redelegation

Players can transfer their Staking assets to another Guild at any time. This is called Redelegation, and can be transferred to another Guild without a lockup period, minimizing losses when transferring to another Guild.

## Earn NCG

Guilds have the right to acquire NCG spent by players belonging to the Guild. This includes:

- Buy
- Sell
- Craft
- Enhancement
- Arena

Additionally, the Guild can obtain NCG collected through various methods within the game (e.g., Adventure Boss).

# Specification

## Phases

### 1. “fill-in” (2024 Q3)

In the fill-in phase, a Planetarium-only guild will be created and take over the Pledge contracts previously provided by Patrons in Portals, etc. At this stage, Planetarium will be the only guild that supplies Mead.

From this phase, the following will be possible:

- Guild will take NCG used in the game.
- Guild will distribute NCG to players according to its own distribution settings.

### 2. Third party Guild (2024 Q4)

Guilds other than Planetarium are created. Guilds can receive network rewards by redelegating Power delegated by players to Validators. These rewards are used to pay players' Gas fees.

From this phase, the following will be possible:

- Anyone can create a Guild.
- Guilds can earn network rewards (e.g., block rewards) by delegating to Validators.
