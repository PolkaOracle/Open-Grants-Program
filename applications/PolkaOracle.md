# PolkaOracle Data Infrastructure

* **Project Name:** PolkaOracle Data Infrastructure
* **Team Name:** Interstellar
* **Payment Address:** 14xrpzaZDWqL7v3nifFKPaaufLVVuAbvKs

## Project Description

PolkaOracle is a scalable, cross-chain, decentralized data transmission platform. Different from other alike oracle projects only providing off-chain data, PolkaOracle can also provide on-chain data feeding. Coupled with its cross-chain technologies, PolkaOracle can integrate on-chain data from other Blockchains into Polkadot ecology for other platforms to use, acting as a pivotal support for the data economics of the entire Polkadot ecology. Furthermore, PolkaOracle also has sophisticated community construction plans as support to Web3.0 applications and development of Polkadot ecology. PolkaOracle can not only push the massive adoption of Blockchain technologies in FinTech, but also can help realizing the in-depth transmission of data for all walks of mankind.

## Polkadot ecology benefits

Based on substrate implementation, PolkaOracle is strongly scalable. It uses Off-chain Worker to interact with on-chain data. With the Polkadot based features and its cross-chain interoperability, it provides safe, reliable and efficient data sources and data analysis, maximizing the benefits of data users and Dapp builders in the true sense. PolkaOracle provides continuous vitality to the Polkadot ecology starting from the liquidity of the underlying data.

## Oracle overview

In Blockchain, Oracle is an agent who helps the blockchain to communicate with multiple external sources, providing accurate and reliable information for on-chain smart contracts. Oracle is not just an off-chain data source itself, but a middleware that queries, validates, and forwards external information, including market data (such as price information), event information (such as real time flight information), or other data sources as measured by sensors. In addition, some Oracles are even capable of sending on-chain information back to external sources. Therefore, Oracle plays an important role during the interaction between the blockchain and the real world.

## Project Details

Substrate offers an excellent framework and development kit that comes in handy:

- The emergence of Substrate has lowered the barrier of blockchain development and shortened the development cycle, enabling developers to concentrate on their commercial implementation. On this basis, PolkaOracle, more professional and detailed in this field, is different from traditional blockchain development, focusing on the secure implementation of data flow.

- Offchainworker can help Oracle to achieve the core functions like excellent data request, acquisition, transmission, but OCW still relies on manual request implementation in voting. PolkaOracle will provide a request library that integrates various functions like OCW and the developer’s DAPP, enabling an interaction of intelligence and convenience between blockchain and the external data.

- In addition to OCW, Substrate also provides a very comprehensive range of different blockchain function pallets. PolkaOracle will expand many custom pallets based on its basic function pallet, which is different from the high transaction fee and low scalability of Ethereum, in this regard, the clear development and cross-chain operability provided by Polkadot provide a better solution for the entire blockchain ecosystem.

## Project structure

Based on the points and resources above, the PolkaOracle team has integrated a very advanced oracle project plan:

### PolkaOracle provides advanced distributed data transfer protocols

Off-chain Worker is a pallet of Substrate 2.0, which allows developers to request safely integrate external data into the blockchain application through RPC or http, websocket request. Data can be transmitted by sending signed transactions to the chain, non-signed transactions extrinsic, or read OCW’s local storage via API, Based on Substrate’s framework, PolkaOracle offers advanced distributed data transfer protocol on the basis of OCW and also complement with each other.Polka Oracle offers a variety of API interface to get the third party off-chain data, to conduct a preliminary screening, comparing and filtering data, ensure the truthfulness, accuracy and real-time data, providing a reliable source of data for the user, all sorts of DAPP or external analysis tools, to implement low cost function of the commercialization of the environment, future customize special parsing API service for advanced users will also be achievable.

<p align="center">
  <img src="https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_workflow.jpg"><br>
  <b>Brief demo of PolkaOracle workflow</b>
</p>

1. When a user initiates a data request, the OCW in the PolkaOracle node will request a third-party verifiable data API (such as the Web Site API) via RPC or http,websocket, or read the local OCW database to obtain the raw data via Substrate's API. After basic screening, comparison and preliminary verification of the data by the node network, the data will be submitted to the trading pool through signed transaction or non-signed transaction (logical verification).

2. Miners pack the transaction data in the trading pool and submit it to the on-chain data storage. All the transaction data submitted will be published on-chain, and then the community users will conduct a referendum to get the final confirmed transaction data and return it to the chain, and the other candidate data will become invalid.

3. If the data submitted by the staking node is incorrect or tampered with, the user can initiate a referendum on prosecution. If the voting result agrees to sanctions, the node submitting the data will be punished with SLASH. The confiscated staking assets will be equally rewarded to network nodes that find data errors.

4. The data submitted to the chain will be confirmed by the whole blockchain. If it is the node of the chain, it will directly read the data on-chain by initiating extrinsics or calling smart contract. If it is other parachain or parathread on Polkadot, it will read the data through XCMP, if it is a heterogeneous chain or an application will request on-chain data through RPC.

5. For application users, they can simplify and speed up data transfer process by deploying smart contracts and voting to be added to the smart contract list by the community.

### PolkaOracle provides a highly compatible contract platform

Thanks to the rapid development of Substrate, PolkaOracle integrates the pallet_evm, pallet_ethereum that are compatible with Ethereum smart contracts and Substrate-based smart contract development platform Ink. Users can customize the data structure they need through the contract components, and even deploy all the logic code in our smart contract module to maximize the use of various data we provide.

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_contract.jpg)

### The main Pallet design and implementation of PolkaOracle

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_pallet.jpg)

The main pallet mainly defines the off-chain data request and data transmission protocol through the OCW. The main functions are stated as follows

1. `OffchainHttpRequestData`

    `Function`：Through OCW, HTTP is used to communicate with the third-party API and obtain the data, then JSON parsing is performed, and the required data is obtained by deserializing the JSON string into the structure

    `Params`: `http url,requeset status,time out`
    `Return`: `DataBuffer`

2. `InputOrGetOffchainStorage`

    `Function`：Input externally obtained data to OCW local database or retrieve required data from it
    `Params`: `InputOrGetFlag,Option<DataBuffer>`
    `Return`: `Result<DataBuffer,Error<T>>`

3. `SendTransactionToChain`

    `Function`: OCW uses four methods: signed transaction, unsigned transaction, unsigned transaction with any account signed payload, unsigned transaction with all account signed payload, and sends the unsigned data to the chain after logical verification
    `Params`: `OffchainAppcrypto,Signature,Option<TransactionSource>(unsignedTransaction),BlockNumber`
    `Return`: `Result<(),Error<T>>`

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_parachain.jpg)

PolkaOracle is linked into the Polkadot ecological network as a parachain and shares the basic consensus of Polkadot. Anyone can build a multi-node Oracle network by deploying and running the PolkaOracle Collector node to provide on-chain/off-chain data with built-in interoperability.

Other platforms on Polkadot ecosystem can access our data through the XCMP protocol.

### PolkaOracle data analysis layer

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_analytics.jpg)

The PolkaOracle data analysis tool will be used as an independent on-chain custom pallet, which can be called or skipped. Various targeted data processing, algorithm calculations, result conversion operations can be customized according to requirements, and useful data can be selected from the huge amount of data. Data will be transmitted on-chain after verification.

### Cross-chain

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_crosschain.jpg)

When polkaOracle transmits data with heterogeneous chains, it needs to initiate RPC via OCW to request to read data on other chains

PolkaOracle node is responsible for the blockchain, scheduling and balancing other external services and has some built-in sub-tasks, performing rpc or web requests, JSON parsing, and data transmissions between heterogeneous chains (BTC, ETH, EOS). Submit cross-chain data to the PolkaOracle network through OCW.

Subtasks can be defined by creating adapters, which are open-sourced external services with minimal Rest API. Programs in any programming language can be implemented simply by adding a small intermediate API in front of the program.

### Data exchange

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_dateexchange.jpg)

Data exchange enables the on-chain data which confirmed by the screening referendum in Polka Oracle network to be traded,  and the data needed by DAPP or other applications can be determined quickly. The on-chain node or the user can initiate a proposal and vote if the requested on-chain data is void. After voting, if the proposal is passed, the new pledge node will collect the data and send it to the chain for a new round of referendum confirmation. Finally, the user will make a second RPC request to read the required data.

The data consumer interacts with the request contract and then selects the most appropriate result data.

If the data consumer does not locate a suitable result, the user can also submit the data to the chain by joining Polka Oracle collectors, so as to provide it to the data consumer. Users who submit data have the opportunity to obtain token rewards, or they can apply to distribute token rewards to data feeders.

### PolkaOrcale provides a mature cross-chain prediction platform

PolkaOracle, a decentralized prediction platform of cross-chain and community governance, is more decentralized and cost-effective than traditional platforms. The reputation system based on NFT identity authentication not only provides users with more reliable, comprehensive and effective reference, but also guarantees the efficiency, security and reward-punishment.

### PolkaOracle Token

POT is the native token in Polka Oracle network, which is used to pay transaction fees and data feedback services to data providers (bottom nodes), as well as to pay for deposits of any on-chain application. In addition, POT holders will be able to vote on proposals from the community and even decide how the ecosystem fund will be used in the PolkaOracle.

PolkaOracle will eventually combine the above functions and be proactive in the Polka ecosystem as a Parachain of Polkadot. In addition, PolkaOracle will make the CallPallet and API interface publicly accessible, so that other Parachains can join the data flow ecology of PolkaOracle by connecting to PolkaOracle CallPallet. PolkaOracle not only has a breakthrough in the technical field, but also has its own achievements in application scenarios because the team firmly belives that the technology is inseparable from the user group.

## The main utilities of POT are as follows

### Governance

Only community members holding POT have the right to participate in the governance of the entire Oracle network, including voting on whether to add a subcontract or system upgrade proposal. In addition, the PolkaOracle can also initiate community proposals to change the entire network, but it must obtain the consent of more than one third of the network nodes.

### Payment

Pot is the only payment medium and value unit in the whole network. The data demander needs to pay the POT to the data provider and the verification node when initiating the data request.

### Deposit

Pot is also the only collateral asset in the whole network. As long as the community members ensure enough pot tokens to meet the hardware requirements of node operation, they can freely join the whole Oracle network and participate in the tasks of data collection, data verification or block packing in the network.

## Polka Oracle application scenarios

Compared with other oracles such as chainlink

1. More decentralized: pledge a certain amount of platform token to become an authentication node, which does not need to be approved by the official, and multiple Oracle machines will also avoid the adverse effects of single / centralized Oracle machine being attacked and bribed;

2. More cost-effective: projects with authentication node qualification consume less platform token when calling oracle;

3. Reputation system based on NFT identity authentication: authentication node has innovative NFT identity token. It can not only effectively prevent witch attacks, but also keep records of the service logs, adoption probability, misconducts and other records of each node on NFT to provide more reliable, comprehensive and effective reference for users;

4. Balanced quotation system combining efficiency, security and reward-punishment scheme: the data provided by the node needs to pass the basic data screening firstly to eliminate abnormal items. Secondly, the data will accept the support or opposition of community users in a short time. Users can use the governance token to participate in the voting. After voting, the data can be reported in a short time. Whistleblowers need to pledge a token to prosecute, long time after the prosecution of the whole network referendum, after successful prosecution, the whistleblower can get the evil node's pledge token as a reward, on the contrary, the successful node and its supporters will get platform token as a reward.

5. Application scenarios are more multi-source: in addition to price feeding services, it can also be applied to forecasting, games, etc., building a bridge between real data and the on-chain world.

6. The official prediction platform will be built in the prediction application: a decentralized platform of cross chain + community governance. The details are described in the basic architecture below.

### 1. Overview

Build a decentralized prediction platform of cross chain + community governance based on PolkaOracle.

### 2. Detailed introduction of business flow chart

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_business01.jpg)

![img](https://raw.githubusercontent.com/PolkaOracle/images/master/polkaoracle_business02.jpg)

1. Prediction initiation and participation

    - We will enable a forum like field which has three parts: proposal area, alternative proposal area and formal prediction area.

    - After users' wallets are connected to the platform, they can initiate proposals in the initial proposal area, and they can also ‘like’ other proposals.

    - The user's proposal needs to follow a certain format, such as setting the title, options, voting currency, voting cycle and end time, and explain why the voting result can not be easily manipulated and can be obtained at the end time, so as to win the support of other users.

    - Users ‘likes’ in the proposal area, the nodes with more likes will enter the alternative proposal area

    - The initial decision is made by the administrator to decide whether it can be entering the official prediction area. In later stage, it is decided by the community governance committee / governance token voting.

    - Enter the voting period and wait for the result after votes end. 

    - After the result comes out, the proposal user uploads the result to the oracle. The result has a period of publicity. If users object, they can sue and then the whole network users will vote again. The result with more votes will be the final result.

2. Result Liquidation

    - In the liquidation stage, the successful prediction user gets the corresponding voting token of the failed prediction user, a certain proportion as the platform gas fee.

    - Distribution of platform transaction fee includes the following three ways:

        - Prediction Leaderboard Award: It will accumulate periodically. The initial period is 7 days, and the later period can be decided by the user's vote.

            - The winning rate ranking is sorted by the predicted winning rate (the basic limit is that users must participate in at least four predictions). The top 10% users with the highest winning rate are weighted and shared according to their winning rate. For example, the winning rate of user a is 90%, that of user B is 85%, and that of user C is 80%. Then user a gets the bonus of the winning rate ranking*（90%/(90%+85%+80%)）

            - Participation ranking: ranked by the number of participating fields, and the top 10% users with the highest number of participating fields are weighted according to the number of participating fields;

            - Comprehensive ranking: ranked by the results of the number of participating Games * winning rate, the top 10% users with the highest comprehensive scores are weighted and shared according to their comprehensive scores. 

        - Lucky Draw Rewards for Prediction Participants.

            Accumulate periodically. Each user has a 1% chance to get 1% of the reward at the beginning of voting. This parameter will be modified by community voting later.

        - Technology development / maintenance costs

            Expenses for technical team development / maintenance.

    - User Income

        - Reward for correct prediction
        
            The majority of the proportion of reward to the successful, and the voting mining awards are shared according to the respective voting proportion of the successful users. The rewards are from the corresponding voting token of the users who have failed to predict
        
        - Vote mining award

            Users can get a certain number of airdrop governance tokens by voting mining.

        - Liquidity mining award

            users can use LP token to mine after providing liquidity support for transactions related to governance token on DEX,

        - Forecast leaderboard award

        - Invite airdrop award

            After the invited users participate in the prediction voting successfully, level 1 will get a% airdrop token award, and level 2 will get B% airdrop award. For example, a = 5, B = 3, and suppose that Bob invites Alice to vote, and Alice spends 100 platform currency to participate in the voting, then Bob gets 5 platform currency. Only when users votes with platform currency.

        - Reward for lucky participant of prediction

            Each user has a 1% chance to get 1% of the reward at the beginning of voting.

### Development Tools

- Applies to

    - IDE / IDE plugin

        VS code

- Requirements

    - programming language

        Rust

## Use Cases of PolkaOracle Data Infrastructure

Through the PolkaOracle to obtain timely and reliable events outside the insured chain, blockchain-based decentralized insurance can realize automatic payment of insurance such as flight delay insurance.

Stablecoins and encrypted derivatives need to frequently obtain off-chain real-time price data. PolkaOracle can obtain reliable data in multiple scenarios in real time and efficiently.

PolkaOracle can provide real-time and reliable currency prices and borrower’s social media information, providing strong support for the dynamic determination of loan interest rates.

The lightweight PolkaOracle interface that can be deployed on multiple chains provides the possibility for decentralized exchanges to realize cross-chain atomic transactions.

## Team Code Repos

* [https://github.com/PolkaOracle/Parachain](https://github.com/PolkaOracle/Parachain)

## Team members 

* Changyou Ye
* Wei Wu
* Jingyu Wang
* Taiqin Wu
* Guozhu Liang
* Jing Zheng
* ...

## Team’s background and experience：

* Wei Wu holds a Master's degree in computer Engineering from MIT. He has 4-years of experience in blockchain core development. He was formerly a senior engineer at Tencent, a core developer at PolkaOracle. He is a senior Substrate Framework early researcher.
 
* Changyou Ye is a senior blockchain full-stack development engineer. He holds a Master’s degree from Tsinghua University. He is also a Substrate runtime developer. He is proficient in distributed financial blockchain development.
 
* Jingyu Wang  has been contributing to several Polkadot ecosystem open source libraries. He has solid software engineering experience and was a core developer in  Huaxin Blockchain Research Institute.
 
* Taiqin Wu has a master’s degree in Economics from Nankai University. He has more than 4 years product/program/project management experience in Blockchain and high-tech industry.

* Jing Zheng is Senior web front-end engineer, capable of developing front-end projects independently and use linux and vim. Proficient in the basic framework of the front-end, be proficient in using webpack, and proficient in git collaboration related software such as gitlab, github and gittee. 

## Linkedln Profiles (Partial)
 
* [Guozhu Liang](https://www.linkedin.com/in/guozhu-liang-lubis-664a981b9/)
* [Jingyu Wang](https://www.facebook.com/jingyu.wang.92123015)
* [Wei Wu](https://www.linkedin.com/in/wei-wu-bob-1b1aa01b9/)
* [Changyou Ye](https://www.linkedin.com/in/chang-you-ye-598242200/)
* [Jing Zheng](https://www.linkedin.com/in/jing-zheng-42324a200/)

## Development Roadmap :nut_and_bolt:

### Overview

- **Total Estimated Duration:** 6 month
- **Full-time equivalent (FTE):** 10 FTE tech team for the busiest periods
- **Total Costs:** 0.5 BTC

### Milestone 1 — Implement functional economics model on Substrate.

* **Estimated Duration:** 2 months
* **Full-time Equivalent (FTE)**: 10
* **Costs:** 0.15 BTC

|Number|Deliverable|Specification|
|:-:|:-:|:-:|
|0a.|License|Apache License 2.0|
|0b.|Documentation|network整个体系结构完整设计描述的文档，将用作公共协议概述的基础|
|0c.|Testing Guide|测试覆盖率为100%(单元测试和集成测试)。测试涵盖所有用例：数据采集、投票、预测、清算等|
|1|OCW|筛选、验证、比对数据后提交到交易池中|
|2|跨链|通过OCW将跨链数据提交到network中|
|3|XCMP|polka网络中的其他链可以获取我们的数据|

### Milestone 2 — Implement functional economics model on Substrate.

* **Estimated Duration:** 2 months
* **Full-time Equivalent (FTE)**: 10
* **Costs:** 0.15 BTC  

|Number|Deliverable|Specification|
|:-:|:-:|:-:|
|1|链上数据分析|自定义数据分析、分类的逻辑|
|2|数据转换领域|筛选确认后的数据可以进行交易|
|3|智能合约|使用智能合约更便利快捷的使用数据|
|4|数据提交|发起提案并提交数据|
|5|通证|质押、奖励等|
|6|治理|参与polkaoracle network的治理|

### Milestone 3 — Implement functional economics model on Substrate.

* **Estimated Duration:** 2 months
* **Full-time Equivalent (FTE)**: 10
* **Costs:** 0.2 BTC

|Number|Deliverable|Specification|
|:-:|:-:|:-:|
|1|预测提案|发起提案|
|2|投票筛选|选择提案进入预测区|
|3|结果采集|结果公示期|
|4|清算|按投票比率进行奖惩|

## Future Development Plans

What do we expect from the future of Polkadot oracle?

### Future technology development

With the recent rapid development of DeFi, it is foreseeable that the blockchain will massively prosper in the future. In order to effectively respond to future market demand, Polkadot oracle will strengthen its own capacity building in the following aspects:

### L2 solution

Due to the inherent limitations of the blockchain system architecture, the L2 solution will play a key role in future data processing, privacy protection and diversity. Therefore, PolkaOracle will actively research leading L2 technologies such as ZK-rollup technology to ensure that the entire oracle system can always meet the diverse and specialized requirements of the application layer.

### Privacy protection technology

As the requirements for privacy protection in the oracle application field become more and more stringent, oracle will continue to expand in the future application field. Therefore, PolkaOracle will focus on research and development of private protection technologies, including homomorphic encryption technology, secure multi-party computing (MPC) technology and zero-knowledge proof.

### Unstructured data support

As of now, oracle projects on the market are mainly designed for structured data, such as market price data. However, the market demand for unstructured data is also huge in the real business environment. Therefore, PolkaOracle will research unstructured data collection, processing and verification technologies in advance to gain a leading competitive advantage.

## Additional Information

* Work has been done so far

    1. We are drafting and verifying the economic model of the PolkaOracle Data Infrastructure.

    1. We are drafting technical specifications and design of runtime modules.

    1. We are building common runtime modules such as multi-asset tokens that will be used in the PolkaOracle Data Infrastructure.

    1. Several custom components needed for the PolkaOracle parachain and also the technical architecture of the parachain.

## Social Channels

- [Medium](https://medium.com/polkaoracle)

- [GitHub](https://github.com/PolkaOracle)

- [Twitter](https://twitter.com/PolkaOracle)

- [Telegram](https://t.me/polkaoracle)

- [Discord](https://discord.gg/RZwW4MN)
