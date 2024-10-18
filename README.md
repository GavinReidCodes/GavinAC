# GavinAC
## About This Project
GavinAC (Gavin Anticheat) is a open source Minecraft anticheat for 1.8.8 servers operating off of Spigot or Paper. The code here is licensed under GPL v3.

## Dependencies List
- ProtocolLib (version 5.0.0 or above is recommended)
- Any Spigot based server software

## (Upcoming) Features List
### Packet Based
GavinAC is going to almost entirely packet based. This is to ensure that GavinAC performs well, doesn't interfere with the main thread much, and overall allows for better checks.

### Lag Compensation
This anticheat will also include lag compensation methods to ensure that players with high latency aren't affected. Here is what methods GavinAC use to do this:

- Transaction Compensation (Uses transaction packets to determine ping, which is used for our lag conpensation)

- World Update Tracking and Compensation (The anticheat saves block updates into a custom world storage class, which is then used to make sure ghost blocks don't affect the anticheat)

### Cloud Checks
Since there are some checks that we would like to keep private (due to cheat developers), we decided to implement cloud checks into GavinAC. Here is a list of checks that will be done in the cloud:

- (Combat) Aim Heuristic Checks

- (Combat) Auto Clicker Heuristic Checks

### Movement Simulation
We plan on adding a system to GavinAC that handles movements and ensures that most cheats can't be used. Here is how it works:

- 1. Get movement packet data

- 2. Emulate Minecraft movement code using the previous position and movement inputs

- 3. Compare it to the packet data, if it doesn't match up almost exactly, they sre probably cheating and are flagged

### Mitigation and Trust Level System
GavinAC is made to correct impossible and possibly illegitimate movements and actions. This is what we can the "mitigation system". This mitigation system also works along with trust levels/factors.

Here is how it works:

- When someone is flagged, their trust violation level will increase.

- When someone performs an action legitimately, their trust violation level will decrease slightly.

- The higher the trust violation level is, the more likely the player is likely to be flagged and mitigated (as they are more untrustworthy).

Keep in mind mitigations should be taken with a grain of salt, as our checks can false flag and mitigate players (not often but possible).
