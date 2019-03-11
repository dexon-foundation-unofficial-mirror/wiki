# DEXON Network Cryptoeconomics

DEXON Foundation  Last Modified 2019/3/4    v6.0

*This document describes the current plan and vision for the DEXON Network platform. While we intend to attempt to realize this vision, please recognize that it is dependent on a number of factors and subject to a wide range of risks. We do not guarantee, represent or warrant any of the statements in this document, because they are based on our current beliefs, expectations and assumptions, about which there can be no assurance due to various anticipated and unanticipated events that may occur. Please know that we seek to achieve the vision laid out in our whitepaper and website, but that you cannot rely on any of it coming true. Blockchain, cryptocurrencies, other aspects of our technology and these markets are in their infancy and will be subject to many challenges, competition and a changing environment.


## Token Allocation
The total supply of DXN tokens is fixed at 4 billion. The genesis token supply is 1 billion DXN and the other 3 billion DXN will be minted as mining rewards after DEXON mainnet launches. The token allocation is shown below:


Figure 1. Token Allocation
* 75% for Miner’s Reward
	For rewarding miners that actively participate in network consensus and smart contract 
             executions on DEXON Network.
* 25% for Genesis Supply 
	The genesis supply will be distributed to 4 parties, including DEXON Foundation / Team and  
private sale token purchasers under different vesting schedules. 


## Mining Model
Nodes that actively participate in validating transactions will get DXN tokens as mining rewards based on DEXON’s Proof of Participation Model. 

### Proof-of-Participation Model
* Validator Eligibility
A node is eligible to join as a validator if its DXN token deposit reaches the threshold of 1 million DXN. The deposit can come from the node itself or from any other accounts that support the node. It takes 24 hours for the deposit to become effective, and another 24 hours for deposit withdrawals to become effective.
* Symmetric Validator Power
The validating power and the probability to be selected as a block producer among all validators are both fair and symmetric, meaning that the expected mining rewards of each validator will be the same as well. 
* Mining Rewards
A validator earns transaction processing fees, gas fees, and mining rewards when it actively produces blocks and acks to other blocks.


## Adaptive Mining Mechanism
DEXON adopts a novel adaptive mining mechanism that can self-adjust the token minting velocity. The token minting velocity is proportional to the participation rate of mining. If the demand of DXN token is strong, it will attract more token holders to participate in mining for rewards, hence the minting velocity will increase, and vice versa. This will make sure the system can keep demand and supply balanced by itself.


The formula of minting velocity is stated below:

_r_ is total supply growth rate (the annual growth rate of total supply), vis node mining velocity (the annual mining rate of each node), and  is mining participation rate (the percentage of deposited tokens in validators relative to current total token circulation). 
Initially, v is 18.75% and will alter based on the total minted tokens under a half-life condition. 
The relation between node mining velocity and minted tokens is shown below:
* v= 18.75% when mainnet launches. 
* v= 9.375% after 1.5 billion DXN tokens are minted. 
* v= 4.6875% after another 750 million DXN tokens are minted,  and so on.
As an example, inniitialy each node can mine 1M * 18.75% = 187.5K DXN tokens per year. As total minted tokens hit 1.5B DXN, the annual mining rate per node will decrease from 18.75% to 9.375%, and as total minted tokens hit 2.25B DXN, the annual per node mining rate will decrease further from 9.375% to 4.6875%, and so on.


Figure 2. Node Mining Velocity Half-Life Threshold

## Mining Rewards in Circulation 
Now, let’s consider the influence of mining participation rate. For example, the genesis supply of DXN token is 1 billion, if 500 millions tokens are deposited in validating nodes, the mining participation rate will be 50%. So the total supply growth rate will be 18.75% * 50% = 9.375%.
The total mining rewards in circulation based on different participation rates (30%, 50%, 70%) is shown in the figure below:


Assuming the mining participation rate is fixed at 50%, r(total supply growth rate) per year is shown below:

Figure 4. Total Mining Rewards in Circulation

## Genesis Allocation
As stated above, the genesis supply is 1 billion DXN and the allocation is shown below:

Figure 5. Genesis Supply Allocation

* 38.5% to Private Sale Purchasers (Genesis allocation, under 1-year vesting)
             For building strategic partnerships with influential industry entities and growing the 
DApps ecosystem.
* 1.5 % to Public Sale Purchasers (Genesis allocation, no lock-up condition)
             For distributing tokens to early developers / users.
* 40% to DEXON Foundation (Genesis allocation, under 4-year vesting)
             For long-term network development funding and governance, advisory, airdrops, etc.
* 20% to Founding team (Genesis allocation, under 4-year vesting)
For incentivising the founding team members and core developers.

### Private Sale (38.5%)
DEXON Foundation only allows world-famous VC firms, crypto funds, and DEXON DApps ecosystem partners to participate in the private sale. The goal of the private sale is to build up partnership relationships and grow the DEXON DApps ecosystem.
According to the purchased amount, a private sale purchaser will be granted an additional bonus of DXN tokens as shown in the figure below. Note that the bonus structure is tier-based and cumulative.
Figure 6. Private Sale Purchaser Additional Bonus
DXN tokens sold in private sale will be under a 1-year lock-up condition. 3 months after mainnet launches, 10% of DXN tokens will be vested, while each month thereafter, an additional 10% of DEX tokens will be vested in the following 10 months. The bonus portion will be vested 12 months after mainnet launch.


The vesting schedule is as follows:
* 3rd - 12th month after mainnet launch: 10%
* 13th month after mainnet launch: bonus portion

For example, if one purchases 10M USD for 100M DXN tokens, his bonus will be as presented below:
* 1-2M tier: 5% bonus, 0.5M DXN tokens
* 2-3M tier: 10% bonus, 1M DXN tokens
* 3-4M tier: 15% bonus, 1.5M DXN tokens
* 4-5M tier: 20% bonus, 2M DXN tokens
* 5M+ tier: 25% bonus, 12.5M DXN tokens
In total, the purchaser will get additional 17.5M DXN tokens as bonus. The vesting schedule would be as shown below:

Figure 7. Private Sale Purchaser Token Vesting Chart

### Public Sale (1.5%)
DEXON Foundation will sell DXN tokens to the public. The goal of public sale is to distribute tokens to early developers and users. The price of each DXN token in the public sale will be 0.2 USD. 
All DXN tokens sold in public sale will be vested when mainnet launches.

### DEXON Foundation Reserved (40%)
DEXON Foundation reserves DXN tokens for long-term network development funding and governance, advisory, airdrop and more. Most of the vested DXN tokens will be distributed to the public in the long run to ensure long-term network decentralization. 
DEXON Foundation’s reserved tokens are under a 4-year vesting schedule. When the mainnet launches, 20% of DXN tokens will be vested, while each year thereafter, an additional 20% of DXN tokens will be vested. The vesting schedule is shown below:
* Mainnet launch: 20% 
* 1st to 4th year after mainnet launch: 20%

### DEXON Founding Team Reserved (20%)
DEXON founding team reserved DXN tokens are to incentivize the founding team members and core developers. These tokens are under a 4-year vesting schedule. When the mainnet launches, 20% of the tokens will be vested, while each year thereafter, an additional 20% of DXN tokens will be vested. The vesting schedule is shown below:
* Mainnet launch: 20% 
* 1st to 4th year after mainnet launch: 20%



## Token Circulation
The total DXN tokens in circulation will gradually increase as mining rewards are minted and the initial token holder’s tokens are vested. 
1. 75% to DEXON Miners (Mining rewards, responsive half-life condition)
2. 25% for Genesis Supply
- 38.5% to Private Sale Purchasers (Genesis allocation, under 1-year vesting)
- 1.5% to Public Sale Purchasers (Genesis allocation, no lock-up condition)
- 40% to DEXON Foundation (Genesis allocation, 4-year vesting)
- 20% to Founding team (Genesis allocation, under 4-year vesting)
Assuming the mining participation rate is fixed at 50%, 30 years after mainnet launch, about 98.8% (3,953,284,807 / 4,000,000,000) of DXN tokens will be in  public circulation. The long-term total token circulation chart is shown below:

Figure 8. Long-Term DXN Tokens in Circulation 


For the first 16 quarters after mainnet launch, the composition of DXN token circulation is shown below:


Figure 9. Short-Term DXN Tokens in Circulation 






## Use of Funds
The funds received from the DXN token sale will be used for three main purposes:
### Technical Development 40%
For DEXON developers / researchers and partnerships with academic research institutions.
### Ecosystem Development 40%
For community building, corporate partnerships, developer conferences, DApps hackathons, business development, branding, etc.
### Operational Costs 20%
For daily operations / network governance / legal / accounting costs of DEXON Foundation.

Figure 10. Use of Funds


## DISCLAIMER
**PLEASE READ THIS DISCLAIMER SECTION CAREFULLY.  CONSULT LEGAL AND FINANCIAL EXPERTS FOR FURTHER GUIDANCE.**
The following information may be incomplete and in no way implies a contractual relationship. While we make every effort to ensure that all information in this Whitepaper is accurate and up to date, such material in no way constitutes professional advice. DEXON Foundation neither guarantees nor accepts responsibility for the accuracy, reliability, or completeness of this content. The content may be subject to change at any time without prior notice. Individuals intending to purchase platform token should seek independent professional advice prior to acting on any of the information contained in this paper.

**Disclaimer – DXN Tokens and DEXON Foundation**
 
1. Not Securities. 
Use and purchase of the DXN Tokens carries significant financial risk.  DEXON Foundation hereby expressly disclaims that the transactions taking place on its platform pertain in any way to an offering of securities in any jurisdiction or that any documents published on its platform are solicitations for investment.
 
2. Security of Platform. 
You acknowledge that information you store or transfer through DEXON Foundation may become irretrievably lost or corrupted or temporarily unavailable due to a variety of causes, including software failures, protocol changes by third party providers, internet outages, force majeure event or other disasters including third party DDOS attacks, scheduled or unscheduled maintenance, or other causes either within or outside DEXON Foundation’s control.  You are solely responsible for backing up and maintaining duplicate copies of any information you store or transfer through DEXON Foundation’ services

3. No Responsibilities for DXN Tokens
Use and purchase of the DXN Tokens carries significant financial risk. DEXON Foundation does not provide token purchase, financial, or legal advice. The documents provided to you cannot substitute for professional advice and independent factual verification. You warrant that you have conducted your own research and analysis, independently verify any information upon which you wish to rely, consider your own personal circumstances and goals, and obtain independent financial advice from appropriate professionals before making any token purchase decision or taking any other action including without limitation purchasing any DXN Tokens. You further acknowledge and agree that DEXON Foundation has no obligation of due diligence or fiduciary duty toward you.
 
4. No Liability.
Neither DEXON Foundation nor any person or entity associated with it, including but not limited to its agents, servants, employees, insurers, attorneys, successors, and assigns, will be liable, whether in contract, tort (including negligence), or otherwise, for any damage, expense, or other loss you may suffer arising out of any use of the DXN Tokens.
 
5. Technology - Sophistication. 
Tokens are often described in exceedingly technical language; a comprehensive understanding of applied cryptography and computer science is required in order to appreciate inherent risks.  You represent and warrant that you have sufficient knowledge, market sophistication, experience, and/or professional advice sufficient to undertake a prudent evaluation of the merits and risks of purchasing the DXN Tokens. You agree to bear sole responsibility for the aforementioned purchase.
 





6. Technology - No guarantee. 
Neither DEXON Foundation nor its affiliates owns or controls any of the underlying software through which blockchain networks are formed. Neither DEXON Foundation nor its affiliates makes any guarantee of functionality, security, or availability of such software and networks.

7. Technology - Forks. 
The blockchain technology underlying tokens is subject to change at any time, including changes in operating rules (commonly referred to as “forks”), and blockchain networks may go offline as a result of bugs, hard forks, or a number of other unforeseeable reasons. Such changes may materially and adversely affect the value or function of the DXN Tokens. You agree that you are fully responsible for monitoring such changes and agree to bear all risks arising therefrom or relating thereto.

8. Technology - Malicious Nodes. 
Some nodes in the DEXON Foundation network may be malicious and attempt to get rewarded without corresponding contribution; also, attackers may try to ruin the DEXON Foundation ecosystem if they only suffer from minimal penalties. We need strong guarantees to protect the network from malicious attacks to ensure that the transactions are secured and the ecosystem is sustainable. Some attacks that could threaten a blockchain network are listed and discussed as follows:
Sybil Attack 
Malicious nodes could create multiple Sybil identities to strive for more rewards or cheat the network. In general, the proof mechanism should have established barriers to prevent Sybil attacks; however, there is no guarantee such barriers will always be successful.
Out-of- Work Attack
While an attacker can control a lot of nodes, the nodes could be used to make some troubles on a distributed computing network. The nodes controlled by malicious attackers could be called zombies. An attack methodology is to ask the zombie nodes to quit or go on a strike at one time. On DEXON Foundation network, the zombie nodes may take AI jobs but fail to complete them or return invalid results. If an AI job is assigned to a group of which most are zombie nodes, the AI job would receive unauthentic results or just simply fail.
Outsourcing Attack
Malicious nodes may outsource their jobs to other nodes, such that they may earn the rewards easily without consuming the corresponding computing power. On DEXON Foundation network, nodes should present their capabilities to strive for taking jobs. Validation of node capabilities based on Proof-of-Intelligence may mitigate the behavior of outsourcing attack because the malicious nodes would lose their jobs if they do not endeavor to execute the same; however, there is no guarantee this approach will always be successful.
Cyber-attacks
In the event of a cyberattack on the DXN Tokens or the DEXON Foundation, the DXN Tokens may be adversely affected. Neither DEXON Foundation nor its affiliates makes any guarantee that it may foresee, prevent, mitigate, or take corrective action in the event of such attack.
 
9. Regulatory Measures
Crypto-tokens are being, or may be overseen by the regulatory authorities of various jurisdictions. DEXON Foundation may receive queries, notices, warnings, requests, or rulings from one or more regulatory authorities from time to time or may even be ordered to suspend or discontinue any action in connection with the DXN Tokens. The development of the DXN Tokens may be seriously affected, hindered, or terminated as a result.
 
10. Illiquidity and Price Volatility
There may not be a demand for DXN Tokens. DEXON Foundation is not responsible for the circulation and trading of DXN Tokens on the market. Tokens, if traded on markets, usually have extremely volatile prices. Fluctuations in price over short periods of time frequently occur, which price may be denominated in Bitcoin, Ether, US Dollars or any other fiat currency. Such fluctuations could result from market forces (including speculations), regulatory changes, technical innovations, availability of exchanges, and other objective factors and represent changes in the balance of supply and demand.
DEXON Foundation does not make any representation or warranty, explicit or implicit, as to the usability or the value of the DXN Tokens. You understand and accept that there is no warranty or assurance that you will receive any benefits through the DXN Tokens.
 
11.  Compliance by Users.
You acknowledge and agree that DEXON Foundation is not responsible for determining whether or which laws, rules, or regulations apply or may apply to your transactions (including, without limitation, any anti-money laundering laws, securities laws and tax laws). You acknowledge and agree that you are in compliance with all such laws, rules, or regulations as may be applicable to your transactions. Without limiting the foregoing, you acknowledge and agree that you are solely responsible for all tax obligations arising from your purchase of the DXN Tokens. You further acknowledge and agree that DEXON Foundation shall not be liable, whether directly or indirectly, for any of your tax obligations.
Applicable law, regulation, and executive orders may require DEXON Foundation to, upon request by government agencies, disclose information regarding your account(s). In the event such disclosure is compelled, you agree that DEXON Foundation may disclose information regarding your accounts. While DEXON Foundation will endeavor to, where commercially reasonable, give you prior notice of such disclosure, DEXON Foundation makes no guarantees that such prior notice will be made. 



