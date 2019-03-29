# Nervos CKB 크립토 이코노미 모델 제안 - (20190328)

## 1. 토큰이코노미의 설계 목표
Public permission-less blockchains are open and distributed systems with diverse groups of participants. A well designed crypto-economics model is to provide incentives so that participants’ pursuit of own economic interests leads to desired emergent behaviors in alignment with the protocol, to contribute to the blockchain network’s success.

비허가형 블록체인(Permission-less)은 다양한 참여자 그룹이 있는 개방형, 분산 시스템입니다. 잘 설계된 암호 경제학 모델은 참여자들이 자신의 경제적 이익을 추구함으로써 프로토콜과 일치하는 원하는 행동을 유도할 수 있도록 인센티브를 제공하는 것입니다.

More specifically, the design of a crypto-economic system has to provide answers to the following questions:

How can the economic model ensure the security of the protocol?
How can the economic model ensure long term sustainability of the protocol?
How can the economic model align the objectives of different actors to grow the value of the protocol network?

구체적으로 설명하자면, 크립토 이코노미 시스템의 설계는 다음과 같은 질문에 대한 답변을 제시해야 합니다. 

경제 모델은 어떻게 프로토콜의 보안을 보장할 수 있는가?
경제 모델은 장기적으로 지속 가능한 프로토콜을 어떻게 유지할 수 있는가?
경제 모델이 프로토콜 네트워크의 가치를 향상하기 위해 서로 다른 행위자들의 목표를 어떻게 일치시킬 수 있는가? 

## 2. 비트코인의 크립토이코노미 모델
The Bitcoin protocol uses its native currency to incentivize miners to validate and produce blocks. The Nakamoto Consensus considers the longest chain as the valid chain, which encourages block producing miners to propagate new blocks as soon as they produce them, validate blocks as soon as they receive them to have the whole network achieve consensus on the global state.

비트코인 프로토콜은 마이너들에게 블록을 검증하고 생성하도록 장려하기 위해 자체적인 화폐를 사용합니다. 나카모토 컨센서스는 가장 긴 체인을 유효한 체인으로 간주합니다. 이 체인은 마이너들이 새로운 블록을 생산하는 즉시 전파하도록 권장하고 전체 네트워크가 글로벌 상태에 대한 합의를 이루기 위해 즉시 블록을 검증하도록 합니다.

The native tokens of the Bitcoin network function both as a utility token and an asset. When bitcoins function as a utility, they can be used to pay transaction fees; when they function as an asset, they can be used to preserve value over time. Those two use cases are often referred to as the “Medium of Exchange” (MoE) use case and the “Store of Value” (SoV) use case. The two use cases are not mutually exclusive. They are both important for the network to function. However, it’s important to study the economic motives of the users of both use cases as a guide to analyze the sustainability of the Bitcoin network.

비트코인 네트워크의 기본 토큰은 유틸리티 토큰과 자산의 기능을 모두 수행합니다. 비트코인이 유틸리티 기능을 수행할 때는 트랜잭션 수수료를 지불하는 데 사용할 수 있습니다. 자산의 기능을 수행할 때는 시간의 경과에 따라 가치를 보존하는 데 사용할 수 있습니다. 이 두 가지 사례는 흔히 “Medium of Exchange (MoE)” 사례와 “Store of Value (SoV)” 사례라고 불립니다. 두 사용 사례는 상호 배타적이지 않습니다. 이 두 사례 모두 네트워크의 기능으로서 작동하는 데 중요합니다. 하지만 비트코인 네트워크의 지속가능성을 분석하기 위한 가이드로서 두 사례 사용자의 경제적 동기를 연구하는 것이 중요합니다.

The Bitcoin protocol constraints the network’s transaction throughput with a fixed block size. Users bid with fees on the limited throughput to have their transactions processed. With this auction like mechanism, transaction fees are determined by the transaction demand - the more demand there is on the network, the higher the transaction fee a user has to pay to beat the competition to have their transaction included.

비트코인 프로토콜은 네트워크의 트랜잭션 처리량이 고정된 블록 크기로 제한합니다. 사용자는 제한된 처리량에 대한 수수료를 지불하여 트랜잭션을 처리합니다. 이 경매 방식과 같은 메커니즘을 사용하면 거래 수수료는 거래 수요에 따라 결정됩니다. 네트워크에 대한 수요가 많을수록 거래를 포함하기 위한 경쟁에서 이기기 위해 사용자가 지불해야하는 거래 수수료가 높아지게 됩니다. 

### 2.1 비트코인의 Medium of Exchange 네트워크
The Medium of Exchange use case views the Bitcoin network primarily as a peer to peer value transfer network. MoE users don’t have to hold bitcoins to benefit from the network - it’s the transactions in themselves that provide value. In fact, there are specialized Bitcoin payment services to provide access to liquidity and allow senders and receivers to acquire and dispose of Bitcoins just in time to perform the value transfer, without having to hold the cryptocurrency. MoE users are not concerned with price, or the movement of price, but care about the fiat equivalent cost of the transaction fees.

Medium of Exchange 사용 사례는 비트코인 네트워크를 주로 피어 투 피어 전송 네트워크로 간주합니다. MoE 사용자는 네트워크로부터 이익을 얻기 위해 비트코인을 보유할 필요가 없습니다. 가치를 제공하는 것 그 자체로의 거래입니다. 즉, 유동성에 대한 액세스를 제공하고 발신자와 수신자가 암호화폐를 보유하지 않고도 가치 이전을 수행할 수 있는 시간에 맞춰 비트코인을 취득하고 처분할 수 있도록 하는 특수한 지불 서비스가 있습니다. MoE 사용자는 가격 변동에 관심을 두지 않지만, 거래 수수료와 화폐의 가치에 관심을 둡니다. 

It’s challenging for Bitcoin to become a dominant MoE network. If the protocol calibrates its block time and the block size, therefore fixing the supply of transactions, the success of the network will necessarily increase the cost of transactions, reducing its competitiveness among other similar purposed blockchains as well as its own forks; If the protocol aims to keep the transaction cost low and increase the supply of transactions with faster block time or bigger blocks, it could compromise both security and decentralization through higher fork rate and increased cost of consensus participation.

비트코인이 지배적인 MoE 네트워크가 되는 것은 쉬운 일이 아닙니다. 프로토콜이 블록 시간과 블록 크기를 조정하여 트랜잭션 공급을 수정하면 네트워크의 성공으로 반드시 거래 비용이 증가하여 다른 유사한 목적의 블록체인 및 자체 포크 간의 경쟁력이 저하됩니다. 이 프로토콜이 트랜잭션 비용을 낮게 유지하고 더 빠른 블록 시간 또는 더 큰 블록을 사용하여 트랜잭션 공급을 늘리기 위해 더 높은 합의 참여 비용과 높아진 포크레이트에 의해 보안 및 탈중앙화 모두를 저해할 수 있습니다.

### 2.2 비트코인의 Store of Value 네트워크
Store of Value users view the Bitcoin network as a protocol to provide security to its native cryptocurrency as an asset that can preserve value over time. They see the Medium of Exchange use case as the necessary function to go in and out of this asset. A store of value user, especially the ones who hold the cryptocurrency for a long time, doesn’t care much about the transaction cost, as they can amortize it over time. They do care about the value of a Bitcoin, which depends on the network’s security and decentralization - if the network becomes less secure and can be attacked easily, it’ll stop being perceived as a store of value and the tokens will lose value; if the network becomes centralized, Bitcoin as an asset no longer has independent value, but has to assume counter-party risk.

Store of Value 사용자는 비트코인 네트워크를 시간이 지남에 따라 가치를 보존할 수 있는 자산으로 기본 암호화폐에 보안을 제공하는 프로토콜로 간주합니다. 그들은 이 자산을 들어오고 나가는 데에 필요한 기능으로 거래소 사용 사례를 보고 있습니다. Store of Value 사용자는 특히 장기간 암호화폐를 보유한 사람은 시간이 지남에 따라 상환할 수 있으므로 트랜잭션 비용에 대해 크게 신경 쓰지 않습니다. 그들은 네트워크의 보안 및 탈중앙화에 의존하는 비트코인의 가치에 더 관심이 있습니다. 네트워크가 덜 안전해지고 쉽게 공격받을 수 있다면 가치 저장소로 인식되는 것을 멈추고 토큰은 그 가치를 잃을 것입니다. 네트워크가 중앙화되면 비트코인은 더 이상 독립적인 가치를 갖지 않지만, Counter-party 위험을 감수해야 합니다.

For Bitcoin to succeed as a SoV network, it has to continue to keep its monetary policy stable and its network secure and decentralized. However, Bitcoin’s monetary policy has a hard cap, and after all the coins are mined, the network can only pay for the miners with transaction fees. It’s still an open question whether this model could be sustainable, especially considering Store of Value networks themselves tend not to produce many transactions.

비트코인이 SoV 네트워크로 성공하기 위해서는 통화정책을 안정적으로 유지하고 네트워크를 안전하게 유지하고 분산시켜야 합니다. 그러나 비트코인의 통화정책은 하드 캡을 가지고 있으며 모든 비트코인이 채굴된 이후 네트워크는 거래 수수료만을 마이너에게 지불할 수 있습니다. 가치 저장소 (Store of Value) 네트워크 자체가 많은 트랜잭션을 생성하지 않는 경향이 있다는 점을 고려할 때, 이 모델이 지속 가능할 수 있는지는 여전히 의문점입니다.

### 2.3 누가 장기적으로 채굴자에게 보상을 줄 것인가？
Security and decentralization are two essential properties of a blockchain network, and they come with a high cost that has to be paid to the operators of the network. Bitcoin’s current model has network security entirely paid with transaction fees after all the coins are mined. However, the MoE users have very limited time exposure to the network’s security risk, therefore won’t be willing to pay for it; the SoV users have prolonged exposure to the network’s security risk and are willing to pay for it, but they produce nearly no transactions.

보안 및 탈중앙화는 블록체인 네트워크의 두 가지 필수 속성이며, 네트워크 운영자에게 지불해야 하는 높은 비용을 수반합니다. 비트코인의 현재 모델은 모든 코인이 채굴된 이후 거래 수수료로 완전히 지불된 네트워크 보안을 가지고 있습니다. 그러나 MoE 사용자는 네트워크 보안 위험에 대한 노출 시간이 매우 제한되어 있으므로, 이에 대한 비용을 지불하려고 하지 않을 것입니다. SoV 사용자는 네트워크의 보안 위험에 장기간 노출되어 있으며 기꺼이 지불할 의향이 있지만 트랜잭션은 거의 발생하지 않고 있습니다.

Bitcoin’s consensus mechanism incentivize miners to recognize the longest chain as the network’s canonical state. Miner’s ongoing supply of hashing power doesn’t only provide security for the current block, but the immutability of all the blocks before it on the canonical chain. Relying on the SoV users to make one time payments for the ongoing security protection they receive from miners is not sustainable.

비트코인의 합의 메커니즘은 마이너에게 네트워크의 표준 상태로 가장 긴 체인을 인식하도록 유도합니다. 마이너의 지속적인 해싱 파워 공급은 현재 블록에 대한 보안을 제공할 뿐만 아니라 표준 체인에서의 모든 블록의 불변성을 제공합니다. 마이너로부터 받는 지속적인 보안 보호에 대해 한번 지불하기 위해 SoV사용자에게 의존하는 것은 지속 가능하지 않습니다.

In a SoV network, relying on inflation to fund network security is more incentive compatible with the users. Inflation based block reward mechanism represents indirect payment from the beneficiary of the network’s ongoing security to the provider of such security, in proportion to the duration that enjoy the service.

SoV 네트워크에서 인플레이션에 의존하여 네트워크 보안에 자금을 공급하는 것은 사용자와 호환되는 인센티브입니다. 인플레이션 기반 블록 보상 메커니즘은 서비스를 즐기는 기간에 비례하여 네트워크의 지속적인 보안 제공자에게 네트워크의 지속적인 보안 수혜자의 간접적인 지불을 나타냅니다.

## 3. 가치 보증 트랜잭션 및 스마트 계약 플랫폼 
Smart contract platforms like Ethereum come with Turing-complete programmability and can support a much wider variety of use cases. The native tokens are typically used to price and pay for the cost of decentralized computation. Like the Bitcoin network, smart contract platforms also have the dual functions of preserving value and performing transactions. They differ from the payment networks in that the value they preserve is not only their own native tokens, but also the internal states of decentralized applications, for example, crypto-assets ownership in ERC20 smart contracts.

이더리움과 같은 스마트 컨트랙트 플랫폼은 튜링 완전한 프로그래밍 기능을 제공하며 훨씬 다양한 사용 사례를 지원할 수 있습니다. 일반적인 토큰은 분산 컴퓨팅 비용에 대한 값을 지불하는 데 사용됩니다. 비트코인 네트워크와 마찬가지로 스마트 컨트랙트 플랫폼에는 가치를 보존하고 거래를 수행하는 이중 기능을 갖추고 있습니다. 그들은 자신이 보유한 토큰뿐만 아니라 ERC20 스마트 계약의 암호화폐 소유권과 같은 분산 된 응용 프로그램의 내부 상태도 보존된다는 점에서 지불 네트워크와 차별점이 있습니다.

Another significant difference is that transactions on smart contract platforms are much more “portable”. It’s much easier to take advantage of the more advanced scripting capability of smart contract platforms, to develop interoperability protocols to move transactions to a more cost effective transactional blockchain and securely settle back to the main “system of record” blockchains.

또 다른 중요한 차이점은 스마트 계약 플랫폼에서의 트랜잭션이 훨씬 더 “이동성”이 있다는 것입니다. 스마트 계약 플랫폼의 고급 스크립팅 기능을 활용하고, 트랜잭션을 보다 비용 효율적인 트랜잭션 블록체인으로 이동시키고 주요 “기록 시스템” 블록체인으로 안전하게 정착할 수 있는 상호운용성 프로토콜을 개발하기가 훨씬 쉽습니다

The economic models of smart contract platforms face similar polarization tendency of payment networks - With their superior interoperable capabilities, smart contract platforms are going to be even more specialized into transactional platforms and preservation platforms. Economically, this bifurcation comes from the fact that the two use cases have different ways of utilizing system resources - transactions consume instantaneous but renewable computation and bandwidth resources, and preservation requires long term occupation of the global state. An economic model optimized for one is unlikely to be optimal for the other.

스마트 계약 플랫폼의 이코노미 모델은 지불 네트워크의 양극화 경향에 직면해 있습니다. 뛰어난 상호 운용 능력으로 스마트 계약 플랫폼은 거래 플랫폼 및 보존 플랫폼으로 전문화될 것입니다. 경제적으로 이 양극화는 두 가지 사용 사례가 시스템 리소스를 활용하는 다양한 방법을 가지고 있다는 사실에서 비롯됩니다. 거래는 순간적이지만 재생 가능한 계산 및 대역폭 리소스를 소비하며 보존은 글로벌 국가의 장기적인 작업을 필요로 합니다. 한 가지에 최적화된 경제 모델은 다른 모델에 최적일 것 같지 않습니다.

Competitive transactional platforms need to prioritize for low transaction cost . Transactional users are willing to accept less-optimal security, because of their only moment-in-time, limited exposure to security risk. They’re willing to accept the possibility of censored transactions, as long as there are options to take their transactions elsewhere. A transactional platform that invests in either security or censorship resistance will have higher cost of transactions, reflected either with higher transaction fees or high capital cost for stakes in a “stake for access” model, making the network less competitive.

경쟁적 트랜잭션 플랫폼은 낮은 거래 비용으로 우선순위를 정해야 합니다. 트랜잭션 사용자는 단 한 번의 순간적이고 제한된 보안 위험 노출에 의해 최적의 보안을 기꺼이 받아들이려고 합니다. 그들은 그들의 거래를 다른 곳으로 가져갈 수 있는 선택권이 있는 한, 검열된 거래의 가능성을 기꺼이 받아들일 것입니다. 보안 또는 검열 저항에 투자하는 거래 플랫폼은 높은 거래 비용을 가지며, “액세스를 위한 스케이킹”모델의 지분에 대한 높은 자본 비용 또는 높은 거래 비용을 반영하여 네트워크의 경쟁력을 떨어뜨릴 것입니다.

This is especially true when a well designed inter-blockchain protocol can allow trust-less state transfers and fraud repudiation of transactions. We already can see examples of transactional users prioritizing cost over security in centralized crypto-asset exchanges and not-so-decentralized blockchains - despite their flaws, they’re still popular because of their transactional efficiency.

이는 잘 설계된 블록 간 프로토콜이 무 신뢰성 상태 이전 및 트랜잭션의 부정행위 거절을 허용할 수 있는 경우 특히 그렇습니다. 우리는 이미 중앙집중식 암호화폐 교환 및 어느 정도 탈중앙화된 블록체인에서 보안에 비해 비용을 우선시하는 트랜잭션 사용자의 사례를 볼 수 있습니다.

## 4. 자산저장
One of the most important use cases for smart contract platforms is to issue tokens to represent ownership of assets. These crypto-assets can have their own communities and markets, and their values are independent from the value of their platform tokens. On the other hand, these assets depend on the platform to process transactions and provide security. Payment networks like Bitcoin can be seen as single asset platforms, where smart contract platforms are multi-asset platforms. Similar to the concept of “Store of Value” in the context of Bitcoin, we call the utility that smart contract platforms preserve the value of its crypto-assets “Store of Assets”.

스마트 계약 플랫폼의 가장 중요한 사용 사례 중 하나는 자산 소유권을 나타내기 위해 토큰을 발행하는 것입니다. 이러한 암호 자산은 자체 커뮤니티와 마켓을 가질 수 있으며, 이들의 가치는 플랫폼 토큰의 가치와 독립적입니다. 반면에 이러한 자산은 트랜잭션을 처리하고 보안을 제공하는 플랫폼에 의존합니다.

Preservation focused smart contract platforms must have a Store of Assets token economics design. The level of platform security has to grow along with the asset value it preserves. Otherwise as asset value grows, it will be increasingly profitable to “double-spend” assets by attacking the consensus process of the platform.

스마트 계약 플랫폼은 다중 자산 플랫폼에서 비트코인과 같은 결제 네트워크는 단일 자산 플랫폼으로 볼 수 있습니다. 비트코인의 맥락에서 "Store of Value” 개념과 마찬가지로, 우리는 스마트 계약 플랫폼이 암호 자산인 "Store of Assets"의 가치를 보존한다는 것을 유틸리티라고 부릅니다. 보전 중심의 스마트 계약 플랫폼은 자산 저장소 토큰 경제 설계가 있어야 합니다. 플랫폼 보안 수준은 보존하는 자산 가치와 함께 증가해야 합니다. 그렇지 않으면 자산 가치가 증가함에 따라, 플랫폼의 합의 프로세스를 공격함으로써 자산을 “이중 지불”하는 것이 더 이익이 발생할 것입니다.

None of the current smart contract platforms are designed as Store of Assets platforms. Their token economics are designed either to facilitate transactions (for example, Ethereum’s native tokens are to pay for the decentralized computation) or to fulfill staking requirements. In either case, the growth in asset value doesn’t necessarily raise miner’s income to provide more security.

현재 스마트 계약 플랫폼 중 어떠한 것도 자산 저장 플랫폼으로 설계되지 않았습니다. 그들의 토큰 이코노미는 거래를 용이하게 하거나 (예, Ethereum의 기본 토큰은 분산 컴퓨팅을 위해 지불해야 함) 또는 스테이킹의 요건을 충족시키기 위해 설계되었습니다. 어느 경우가 되었든, 자산가치의 증가는 더 많은 보안을 제공하기 위해 반드시 마이너의 수입을 올리는 것이 아닙니다.

Every multi-asset platform is an ecosystem of independent projects. The security of the platform can be seen as “public goods” that benefit all projects. To make the ecosystem sustainable from a security point of view, there has to be a clear mechanism that the platform captures the economic success of the ecosystem to raise its own level of security. In other words, a Store of Assets platform has to be able to translate the demand of crypto-assets to the revenue of its miners, often through raising the value of the native tokens that miners are compensated in.
Otherwise, the platform’s level of security becomes the ceiling how valuable the assets can become. When the value of an asset rises such that typical transactions can no longer be sufficiently protected by the platform, the liquidity would dry up and demand on the asset will fade.
Decentralized multi-assets smart contract platforms have to be Store of Assets to be sustainable.

모든 다중 자산 플랫폼은 독립적인 프로젝트의 생태계입니다. 플랫폼의 보안은 모든 프로젝트에 이익이 되는 "공공재"로 간주 될 수 있습니다. 생태계를 보안 관점에서 지속할 수 있게 하기 위해서는 플랫폼이 자체적인 보안 수준을 높이기 위해 생태계의 경제적 성공을 포착하는 명확한 메커니즘이 있어야 합니다. 즉, 자산 저장소는 마이너가 보상받는 토큰의 가치를 높이기 위해 암호 자산의 수요를 마이너의 수익으로 변환할 수 있어야 합니다. 
그렇지 않으면 플랫폼의 보안 수준은 자산의 가치가 얼마나 높은지를 결정하게 됩니다. 일반적인 거래가 더이상 플랫폼에 의해 충분히 보호될 수 없을 정도로 자산의 가치가 상승하면 유동성이 고갈되고 자산에 대한 수요가 감소할 것입니다.

## 5. 탈중앙화 및 상태 제한의 요구

Like other long term store of value systems, a Store of Assets platform has to be neutral and free of risks of censorship and confiscation. These are the properties that made gold the world’s favorite the store of value for thousands of years. For open, permission-less blockchain networks, censorship resistance comes down to having the broadest consensus scope with a low barrier for consensus and full node participation. Comparing to payment networks, running a full node for a smart contract system is more resource intensive, therefore a Store of Assets platform has to take measures to protect the operating cost of full nodes to keep the network sufficiently decentralized.

장기적인 가치저장을 지닌 타 시스템처럼 ‘자산 저장’ 플랫폼은 중립성을 유지해야 하며 검열 및 몰수의 위험이 없습니다. 이러한 조건으로 인해 금은 수천 년 동안 세계에서 가장 가치 있는 가치 저장 수단이 되었습니다. 완전 공개된 비허가형 블록체인 네트워크의 경우 검열에 저항하는 능력은 주로 광범위한 글로벌 합의에서 비롯되며 풀 노드 참여에 대한 진입장벽은 충분히 낮습니다. 페이먼트 네트워크와 비교할 때 스마트 계약 플랫폼은 풀 노드를 실행하는데 많은 리소스가 필요하므로 ‘자산저장’ 플랫폼은 풀 노드의 운영비용을 유지 관리하여 네트워크를 분산된 상태로 유지해야 합니다.

Both Bitcoin and Ethereum throttle transaction throughput to make sure participation is not limited to only “super computers” — Bitcoin throttles on bandwidth and Ethereum throttles on computation. However, they haven’t taken effective measures to contain the ever growing global state necessary for consensus participation and independent transaction validation. This is especially a centralization force for high throughout smart contract platforms, where the global state grows even faster.

비트코인과 이더리움의 TPS의 경우 참가자가 ‘슈퍼컴퓨터’를 가질 뿐만 아니라 비트코인은 대역폭을 제한하고 이더리움 네트워크는 컴퓨팅 능력을 제한합니다. 그러나 효율적인 방식을 채택하지 않았으며 컨센서스 참여 및 거래 검증이 필요한 지속적으로 성장하는 전체 상태를 채택했습니다. 특히 전체적인 스마트 계약 플랫폼은 매우 집중된 수요를 가지고 있으며 전체 상태는 더더욱 빠르게 성장할 것입니다.

In Bitcoin, the global state is the UTXO set. Bitcoin doesn’t control the growth of the size of the UTXOs directly, but every new UTXO adds overhead to the transaction where it’s created, making the transaction more expensive.

비트코인에서 글로벌 상태는 UTXO의 집합입니다. 비트코인은 UTXO 크기의 성장을 직접 제어하지는 않지만 새로운 UTXO가 발생할 시 각각 트랜잭션 비용이 증가합니다.

In Ethereum, the global state is represented with the EVM’s state trie, the data structure that contains the balances and internal states of all accounts. When new accounts or new contract values are created, the size of the global state expands. Ethereum charges fixed amounts of Gas for inserting new values into its state storage and offers fixed amounts of Gas as transaction refund when values are removed. Ethereum’s approach is a step in the right direction, but still has several issues:

이더리움에서 전체 상태는 EVM의 상태 트리로 표시됩니다. 이 상태 트리는 모든 계정의 잔액과 내부 상태를 포함하는 데이터 구조입니다. 새 계정이나 새로운 스마트 계약 값을 만들면 전체 상태의 크기가 커집니다. 이더리움은 새로운 데이터를 입금할 때 고정 Gas 비용이 지불되고 또한 데이터 제거 시 Gas를 거래 환불로 청구됩니다. 이더리움 접근법은 올바른 방향으로 나아가는 단계이지만 여전히 몇 가지 문제가 있습니다.

the growth of the global state is not bounded in any way and can grow infinitely, therefore there’s no certainty in the cost of full node participation
the system raises one-time revenue for expanding the state storage, but miners and full nodes have to bear the expense of storage over time
there’s no obvious reason why the cost of expanding storage should be priced in fixed Gas amounts, which is used to price a unit of computation
the “pay once, occupy forever” state storage model gives very little incentive for users to voluntarily clear state and reduce the size of global state

전체 상태의 성장에는 제한이 없으며 데이터가 무한으로 증가할 수 있으므로 풀 노드의 참여 비용의 불확실성이 있습니다.
이 시스템은 확장된 상태 스토리지에 대해 일회용 요금을 부과하지만, 채굴자와 풀 노드는 장기적인 스토리지 비용을 부담해야 합니다.
확장된 스토리지 비용이 고정 Gas 가격이 왜 고정되어야 하는 명확한 이유가 없습니다. (Gas의 계산단위가 가격을 책정하는 데 사용됩니다)
‘일회용 지불 및 영원한 점령’된 상태 저장 모델의 사용자가 자발적으로 상태를 지우고 전체 상태의 크기를 줄이려는 인센티브 동기부여가 매우 적습니다.


The Ethereum community is actively working on this problem, and the leading solution is to charge smart contract “state rent” — contracts have to periodically pay fees based on the size of its state. If the rent is not paid, the contract goes to “hibernation” and not accessible before the payment is current again. We see several difficult-to-solve problems with this approach:

이더리움 커뮤니티는 이 문제에 적극적으로 대응하고 있습니다. 최고의 해결책은 스마트 계약의 ‘상태 임대’를 청구하는 것입니다. 계약은 상태의 크기에 따라 정기적으로 지불해야합니다. 임대료가 지불하지 않으면 계약은 ‘휴면 상태’가 되어 임대료를 지불할 때까지 실행할 수 없습니다. 이 방법에는 해결하기 어려운 몇 가지 문제가 있음을 알 수 있습니다.

many contracts, especially popular ERC20 contracts, represent decentralized communities and express asset ownership of many users. It’s a difficult problem to coordinate all the users to pay for state rent in a fair and efficient way.
even a contract is current on its rent payment, it still may not be fully functional because some of its dependent contracts may be behind on their payments.
the user experience for contracts with state rent is sub-optimal

• 많은 계약 중 특히 ERC-20 계약은 분산된 커뮤니티를 대표하며 많은 사용자의 자산 소유권을 나타냅니다. 모든 사용자가 공정하고 효율적으로 조율하는 것은 어려운 문제입니다.
• 계약의 임대료를 지불 되더라도 불러야 할 다른 계약이 지불되지 않았기 때문에 계약의 실행이 안 될 수 있습니다.
• 임대를 사용하는 계약에 대한 사용자 경험은 차선책입니다.

We believe a well designed mechanism to regulate the state storage has to be able to achieve the following goals:
the growth of the global state has to be bounded to give predictability for full node participation. Ideally, the cost is well within the range of non-professional participants to keep the network maximally decentralized and censorship resistant.
with bounded growth of the global state, the price for expanding it and the rewards for reducing it should be determined by the market. In particular, it’s desirable to have the cost of expanding state storage higher when it’s mostly full, and lower when it’s mostly empty.
the system has to be able to continuously raise revenue from its state users to pay miners for providing this resource. This serves both purposes of balancing miner’s economics and providing incentives for users to clear unnecessary states sooner than later.

우리가 생각한 상태 저장 메커니즘 설계는 다음 목표 달성과 같습니다.

풀 노드 참여의 진입장벽에 대한 예측 가능성을 제공하려면 전체 상태의 성장이 제한되어야 합니다. 원칙적으로 비전문가 참가자가 네트워크의 탈중앙화 및 검열 저항성을 유지할 수 있는 수준까지 비용을 제어할 수 있습니다.
전체 상태의 제한적인 성장으로 가격의 상승과 하락은 시장에 의해 결정될 것입니다. 특히 상태 저장 공간이 거의 가득 차면 상태 저장 비용을 늘려야 하며 저장 공간이 비어있는 경우 비용을 줄여야 합니다.
이 시스템은 채굴자들이 자원을 제공하기 위해 상태 저장 사용자는 임대료를 끊임없이 지불해야합니다. 이는 사용자가 불필요한 조건을 제거하도록 동기를 부여하면서 채굴자의 경제적 수입의 균형을 유지하는데 도움이 됩니다.

Just like how Bitcoin throttles and forces pricing on bandwidth, and Ethereum throttles and forces pricing on computation, to keep a blockchain network long term decentralized and sustainable, we have to come up with a way to constrain and price the global state. This is especially important for preservation focused, Store of Assets networks, where usage of the network is not about transactions that mostly happen off-chain, but the cost of ongoing occupation of the global state.

블록체인 네트워크의 장기적인 탈중앙화와 지속 가능성을 유지하기 위해 비트코인은 대역폭을 제한하고 이더리움은 컴퓨팅 가격을 제한하는 것과 마찬가지로 전체 상태의 제약과 가격 정책을 제안해야 합니다. 이는 자산 보호에 중점을 둔 ‘자산저장’플랫폼은 오프체인에서 발생하는 대부분의 트랜잭션에 중점을 두지 않고 전체 상태의 지속적인 비용에 중점을 두고 있습니다.

## 6. Nervos CKB의 이코노미 모델

The Nervos Common Knowledge Base (Nervos CKB for short) is a preservation focused, “Store of Assets” blockchain. Architecturally, it’s designed to best support on-chain state and off-chain computation; economically, it’s designed to provide sustainable security and decentralization. Nervos CKB is the base layer of the overall Nervos Network.

Nervos Common Knowledge Base (Nervos CKB)는 가치 저장하는데 중점을 둔 ‘자산저장’블록체인 입니다. 구조적으로 이는 온체인에서 상태 처리 및 오프체인 컴퓨팅을 가장 적합한 플랫폼입니다. 경제적으로 지속가능한 보안 및 탈중앙화를 제공하는 것입니다. 또한 Nervos CKB는 전체 네트워크의 베이스 레이어입니다.



### 6.1 네이티브 토큰

The native token for the Nervos CKB is the “Common Knowledge Byte”, or “CK Byte” for short. The CK Bytes represent cell capacity in bytes and they give owners the ability to occupy a piece of the blockchain’s overall global state. For example, if Alice owns 1000 CK Bytes, she can create a cell with 1000 bytes in capacity, or multiple cells that add up to 1000 bytes in capacity. She can use the 1000 bytes to store assets, application state, or other types of common knowledge.

Nervos CKB의 네이티브 토큰의 이름은 ‘Common Knowledge Byte’ 약칭 ‘CK Byte’라고 합니다. CK Byte는 Cell 공간을 나타내며 소유자는 블록체인의 전체 상태를 이용할 수 있습니다. 예를들어 Alice에 1000 CK Byte가 있으면 하나의 1000 Byte의 공간 또는 최대 1000 Byte의 여러 개의 Cell을 만들 수 있습니다. 1000개의 Byte를 사용하여 가치저장 및 App 상태 또는 다른 유형의 데이터를 저장할 수 있습니다.

A cell’s occupied capacity could be equal to or less than its specified capacity. For example, for a 1000 byte cell, 4 bytes would be used to specify its own capacity, 64 bytes for the lock script and 128 bytes for storing state. Then the cell’s current occupied capacity is 196 bytes, but with room to grow up to 1000 bytes.

Cell이 차지하는 공간은 지정된 공간관 같거나 작아야 합니다. 예를 들어 1000Byte의 Cell의 경우 4 Byte를 사용하여 자기만의 공간을 지정하고 잠금 스크립트는 64 Byte를 사용하여 상태 저장은 128 Byte를 사용합니다. 따라서 Cell은 실제로 196 Byte 차지하지만 1000 Byte까지 확장할 여지는 충분합니다.

### 6.2 토큰 발행 정책

There are two types of native token issuance. The “base issuance” has a finite total supply with a Bitcoin like issuance schedule — the number of base issuance halves approximately every 4 years until all the base issuance tokens are mined out. All base issuance tokens are rewarded to the miners as incentives to protect the network.
The “secondary issuance” is designed to collect state rent, and has issuance rate that’s constant over time. After base issuance stops, there will only be secondary issuance.

네이티브 토큰 발행 정책에는 두 가지 유형이 있습니다. ‘기본발행’은 총공급량이 제한되어 있으며 발행정책은 비트코인과 유사합니다. 기본 발행 수량 토큰이 채굴이 끝날 때 까지 4년마다 토큰 발행량이 반으로 줄어듭니다. 모든 ‘기본발행’ 토큰은 네트워크 보호를 위한 인센티브로 채굴자에게 기여하는 방식입니다. 
‘세컨드 발행’은 상태 임대료를 위한 고안된 것이며 매년 발행량은 일정합니다. ‘기본 발행’이 끝난 뒤 ‘세컨드 발행’은 계속됩니다.

### 6.3 Nervos DAO 및 상태 임대 설계를 위한 세컨드 발행
Since the native tokens represent right to expand the global state, the issuance policy of the natives tokens bounds the state growth. As state storage is bounded and becomes a scarce resource like bandwidth in Bitcoin and computation throughput in Ethereum, they can be market priced and traded. State rent adds the necessary time dimension to the fee structure of state storage occupation. Instead of mandating periodic rent payments, we use a two step approach as a “targeted inflation” scheme to collect this rent:

네이티브 토큰은 전체 상태를 차지할 수 있는 권한을 나타내므로 토큰 발행 정책은 전체 성장을 제한합니다. 상태 저장이 제한적으로 설계된다면 희소 자원이 되므로 비트코인의 대역폭과 이더리움의 컴퓨팅 처리량과 같으며 시장에서 가격을 책정하고 거래할 수 있습니다. 상태 임대료는 상태 점유에 의해 비용 구조를 만들며 필요한 시간 차원을 증가시킵니다. 우리는 두 가지 단계를 ‘목표 인플레이션’ 프레임 위크로 사용하여 정기적인 임대료를 부과하는 대신 임대료를 받습니다.

On top of the base issuance, we add the secondary issuance which can be seen as “inflation tax” to all existing token holders. For users who use their CK Bytes to store state, this recurring inflation tax is how they pay state rent to the miners.
However, we have also collected rent from the CK Bytes that are not used to store state, and we need to return to them what we collected. We allow those users to deposit and lock their native tokens into a special contract called the NervosDAO. The NervosDAO receives part of the “secondary issuance” to make up for the otherwise unfair dilution.

• ‘기본발행’ 기반으로 우리는 ‘세컨드 발행’에서 모든 토큰을 보유하는 사람에게 ‘인플레이션 세금’을 추가했습니다. CK Byte 상태 저장을 사용하는 사용자의 경우 이 정기적인 인플레이션 세금은 채굴자에게 상태 임대료와 같은 지불하는 방식입니다.
• CK Byte 상태 저장을 사용하지 않는 소유자도 임대료를 청구해야 합니다. 그래서 우리는 이런 사용자들이 지불하는 임대료를 반환 해야 합니다. 우리는 이 사용자들이 가지고 있는 네이티브 토큰을 Nervos DAO 라고 부르는 특별 계약에 락업을 허용합니다. Nervos DAO 는 불평등으로 인한 문제들을 위해 ‘세컨드 발행’으로 보상을 줄 것입니다.

Let’s suppose at the time of a secondary issuance event, 60% of all CK Bytes are used to store state, 35% of all CK Bytes are deposited and locked in the NervosDAO, and 5% of all CK Bytes are kept liquid. Then 60% of the secondary issuance goes to the miners, 35% of the issuance goes to the NervosDAO to be distributed to the locked tokens proportionally. The use of the rest of the secondary issuance — in this example, 5% of the that issuance — is determined by the community through the governance mechanism. Before the community can reach agreement, this part of the secondary issuance is going to be burned.

‘세컨드 발행’에서 모든 CK Byte의 60%가 상태 저장으로 사용되며 모든 CK Byte의 35%가 Nervos DAO 계약에 락업 되고 나머지 CK Byte의 5%는 유동성을 위해 유지시킵니다. 세컨드 발행이 블록 보상을 진행할 때 60% 세컨드 발행의 인센티브가 채굴자에게 가며 35%는 Nervos DAO 계약에 락업된 사용자에게 할당되고 나머지 5%는 거버넌스 메커니즘을 통해 커뮤니티에 의해 결정되며 거버넌스가 합의에 도달하기 전에 소각됩니다.

For long term token holders, as long as they lock their tokens in the NervosDAO, the inflationary effect of secondary issuance is only nominal. For them it’s as if the secondary issuance doesn’t exist and they’re holding hard-capped tokens like Bitcoin.

장기적인 토큰 보유자의 경우 토큰 락업이 Nervos DAO 계약에서 ‘세컨드 발행’의 인플레이션 효과는 명목상으로 적용됩니다. 그들은 ‘세컨드 발행’ 이 존재하지 않는 것처럼 그들이 보유한 토큰은 비트코인과 같은 하드 캡 디자인을 가집니다.

### 6.4 채굴자 보상

Miners are compensated with both block rewards and transaction fees. They receive all of the base issuance, and part of the secondary issuance. In the long term when base issuance stops, miners still receive state rent income that’s independent of transactions but tied to the adoption of the common knowledge base.

채굴자는 두 종류의 블록 보상 및 거래 수수료를 받습니다. 그들은 모든 ‘네이티브 발행’과 일부 ‘세컨드 발행’을 얻을 것입니다. 장기적으로 채굴자들은 ‘네이티브 발행’이 끝나도 상태 임대료로 수입을 얻을 수 있습니다.

### 6.5 트랜잭션 수수료 지불

A decentralized blockchain network’s transaction capacity is always limited and its resources are constrained. Transaction fees serve the dual purposes of establishing a market for the limited transaction capacity and as protection against spams. In Bitcoin, transaction fees are expressed with the difference between the outputs and inputs; In Ethereum, processing transactions requires miners to perform computations that can’t be estimated efficiently, therefore transaction fees are expressed as cost of unit of computation or as “gas price”. Ethereum transactions include both properties of “gas price” and “gas limit”, and the real transaction fee is multiplied by amount of gas used, up to the specified .

탈중앙화 블록체인 네트워크의 트랜잭션 처리량이 제한적이며 리소스도 제한적입니다. 트랜잭션 수수료에는 두 가지 목적이 있습니다. 하나는 제한된 트랜잭션 처리량을 위한 시장 구축입니다. 다른 하나는 악의적인 공격을 방지하는 것입니다. 비트코인에서 트랜잭션 수수료는 출력과 입력의 차이로 표현되며 이더리움에서는 트랜재션 처리 시 채굴자가 효과적으로 예측할 수 없는 계산을 수행해야 하므로 트랜잭션 비용은 계산된 단위 비용 또는 ‘Gas price’로 표시됩니다. 이더리움 트랜잭션에는 gas price와 gas limit 속성이 포함됩니다. 실제 트랜잭션 비용에는 gas price에 사용된 gas 금액을 곱한 값이 있지만, gas limit의 상한값을 초과하지 않습니다.

To ensure decentralization, the Nervos CKB restricts both computation and bandwidth throughput, effectively making it an auction for users use those system resources. When submitting a transaction, the user can leave the total input cell capacities exceeding the total output cell capacities, leaving the difference as transaction fees expressed in the native tokens, payable to the miner that creates the block containing the transaction.

탈중앙화를 보장하기 위해 Nervos CKB는 컴퓨팅 및 대역폭의 처리량을 제한하며 사용자가 이러한 시스템 자원을 사용하고자 할 때 효과적인 경매시장이 될 수 있습니다. 사용자가 트랜잭션을 제출하면 제출된 총 입력이 Cell의 총 출력을 초과해야 하며 그 차이는 기본 토큰으로 지불된 트랜잭션 수수료로 처리되고 컨펌된 트랜잭션은 채굴자에 지불됩니다.
The number of units of computation (called “cycles”) also needs to be submitted as part of the transaction. Nervos CKB is an “off-chain computation, on-chain verification” platform, therefore the cycles of computation are known by the client who submits the transaction. When producing blocks, miners order transactions based on both transaction fees and the number of computation cycles necessary for transaction validation, maximizing its per-computation-cycle income within the computation and bandwidth throughput restrictions.

계산된 단위 수량(계산 주기의 수)도 트랜잭션의 일부로 제출해야 합니다. Nervos CKB는 ‘오프 체인 컴퓨팅, 온체인 검증’을 위한 플랫폼이므로 트랜잭션을 제출하는 클라이언트는 계산 주기의 수를 알고 있습니다. 블록생성 시점에서 채굴자는 트랜잭션 주기 및 트랜잭션 검증에 필요한 계산 주기를 기반으로 트랜잭션을 공식화하여 계산 주기당 수익 및 대역폭 처리량 한계를 극대화합니다.

In the Nervos CKB, the transaction fees can be paid with the native tokens, user defined tokens or a combination of both.

Nervos CKB에서는 네이티브 토큰 또는 ‘사용자 정의 토큰’을 사용하여 거래 수수료를 지불할 수 있으며 이 두 가지 조합을 사용하여 수수료를 지불 할 수도 있습니다.

### 6.6 '사용자 정의 토큰 UDT’를 사용한 트랜잭션 수수료

Users are also free to user other tokens (for example, stable coins) to pay transactions fees, a concept known as “Economic Abstraction”. Note that even without explicit protocol support, it’s always possible to have users make arrangements with miners to pay transaction fees in other tokens outside of the protocol. This is often seen as a threat for many platforms — if the platform’s native tokens are purely to facilitate transactions, this would take away its intrinsic value and cause a collapse.

사용자는 스테이블 코인과 같은 다른 토큰을 트랜잭션 비용을 지불하는 데 자유롭게 사용할 수 있습니다. 이 개념은 ‘경제적인 추상화’입니다. 명확한 계약 지원 없이도 사용자는 채굴자가 계약 외의 토큰 지불 거래 수수료를 사용할 수 있도록 항상 준비할 수 있습니다. 이는 종종 많은 플랫폼에서 위협을 간주합니다. 플랫폼 네이티브 토큰이 순전히 트랜잭션을 용이하게 하는 경우 시스템의 고유 가치를 박탈되고 붕괴로 이어질 수 있습니다.

With the Nervos CKB, we embrace economic abstraction and the benefits it brings. Since the intrinsic value of the native tokens is based not on transaction payment, economic abstraction doesn’t pose a threat to the stability of our economic model. We do expect, however, the native tokens themselves are going to be the payment method of choice for vast majority of users and use cases — the native tokens are going to the most widely held tokens in the Nervos ecosystem, and everyone who owns assets necessarily owns the Nervos natives tokens as state storage capacity that the assets occupy.

Nervos CKB를 통해 우리는 경제 추상화가 가져오는 이점을 받아들입니다. 네이티브 토큰의 본질적인 가치는 지불 수수료를 기반으로 하지 않기 때문에 경제적 추상화는 우리 경제 모델에 위협이 되지 않습니다. 그러나 네이티브 토큰이 대부분의 사용자 및 응용 프로그램에 기본 설정된 지불 방법이 되기를 바랍니다. 네이티브 토큰은 Nervos 생태계에서 가장 널리 사용되는 토큰이 될 것입니다. 자산을 소유한 모든 사람이 Nervos의 네이티브 토큰을 소유해야 하기 때문입니다. 자산 자체가 특정 저장 공간을 가지고 있기 때문에 네이티브 토큰은 저장 공간의 상태에 해당합니다.

detailed analysis on transaction payments, please see Appendix 1.
더 많은 수수료 분석 같은 경우는 부록 1에 자세히 나와 있습니다.

## 7. 가치저장을 위한 이코노미 모델

The economic model of the Nervos CKB is designed specifically to preserve assets and other types of common knowledge. Let’s bring back the 3 high level design goals and examine our design in this context:

How can the economic model ensure the security of the protocol?
How can the economic model ensure long term sustainability of the protocol?
How can the economic model align the objectives of different actors to grow the value of the protocol network?

Nerovs CKB의 이코노미 모델은 자산 가치와 다양항 유형의 데이터를 보존하기 위해 설계되었습니다. 다음 세 가지 중요한 이코노미 모델 설계 목표를 돌이켜 봅시다.

이코노미 모델을 통해 어떻게 프로토콜의 안정성을 보장할 수 있을까요?
이코노미 모델을 통해 어떻게 장기적으로 지속 가능한 모델을 보장할 수 있을까요?
이코노미 모델을 통해 서로 다른 주체들이 전체 네트워크 가치를 증가시키는 공동의 목표를 어떻게 구축할 수 있을까요?

### 7.1 프로토콜의 안정성및 지속성

The main design choices we made to ensure security of the Nervos CKB as a “Store of Assets” protocol are:
Our native tokens represent claim to capacity in the state storage. This means the demand to holding assets on the platform directly puts demand on owning the native tokens. This creates an effective value capture mechanism into the native tokens from the assets they preserve. This is the only sustainable way that a “Store of Assets” platform can grow its security budget over time, instead of entirely basing it on speculation and altruism.
The secondary issuance makes sure miner compensation is predictable and based on preservation demand instead of transactional demand. It also eliminates potential incentive incompatibility of the Nakamoto Consensus nodes after block reward stops. The NervosDAO serves as the counter-force to the inflationary effects of secondary issuance, to ensure long term token holders are not diluted by this issuance.

Nervos CKB가 ‘가치저장’ 프로토콜을 보장하기 위한 주요 아키텍처 설계는 다음과 같습니다.
네이티브 토큰은 상태 저장 공간을 나타냅니다. 즉 플랫폼에서 자산을 보유하는 경우 네이티브 토큰이 있어야 합니다. 플랫폼에 자산을 보유하는 것은 네이티브 토큰에 대한 수요를 창출하는 것 과 동일하므로 네이티브 토큰에 효과적인 가치 포획 메커니즘을 생성합니다. 이는 ‘가치저장’플랫폼이 투기 및 이타주의 시간에 따라 지속적으로 보안 예산을 개속 증가시킬 수 있는 유일한 방법입니다.
세컨드 발행은 채굴자에 대한 보상이 예측이 가능하고 거래 가능의 수요가 아닌 가치 저장으로 기반됩니다. 또한 블록 보상이 끝난 뒤 나카모토 컨센서스의 컨센서스 노드와 같은 인센티브 충돌 문제를 제거합니다. NervosDAO는 오랜 기간 동안 토큰을 보유한 사람들이 ‘세컨드 발행’으로 희석되지 않도록 세컨드 발행의 인플레이션 효과에 대한 반대 세력의 역활을 합니다.

For a purpose of keeping the network decentralized and censorship resistant, we believe it’s important to limit the resource requirements of consensus and full nodes. We protect the operating cost of nodes by regulating the throughput of computation and bandwidth, similar to how it’s accomplished with Bitcoin and Ethereum. We regulate the state storage with a combination of a “cap and trade” pricing scheme and opportunity cost based cost model for storage users.

네트워크의 탈중앙화 및 검열 저항 기능을 유지하려면 풀 노드를 되기 위해 필요한 참여 진입장벽을 낮추는 것을 매우 중요하다고 생각합니다. 우리는 비트코인 및 이더리움의 구현과 비슷하게 계산 및 대역폭 처리량을 조정하여 노드의 운영 비용을 보호합니다. 상태 스토리지는 ‘용량제어’ 가격 프레임 워크 및 스토리지 사용자의 비용 모델을 기반으로 두 방식을 통해 기회비용을 제어합니다.

### 7.2 네트워크의 참가자 유형에 대한 이익 일관성

In a typical smart contract platform, participants of the network have different interests — users want cheaper transactions, developers want adoption of their applications, miners want higher income, and holders want appreciation of their tokens. Those interests are not well aligned, and oftentimes in conflict — for example, more adoption won’t give cheaper transactions (they’ll be more expensive as more demand is put on the blockchain); cheaper transactions won’t give more income to the miners; higher token price won’t help with transaction cost (the opposite could happen if users don’t adjust their local transaction fee setting). Decentralized computation platforms provide value through processing transactions. The price of their tokens doesn’t materially change the intrinsic value of the network. For example, Ether’s price doubling doesn’t increase or decrease Ethereum’s intrinsic value as a decentralized computation platform. Assuming the gas price doesn’t change, a user can accomplish the same task with the same cost on the network. This makes token holders of Ethereum only take the role of an investor, instead of active contributors.

일반적인 스마트 계약 플랫폼에서 네트워크 참여자마다 다른 의도가 있습니다. 사용자는 저렴한 거래 수수료를 원하고 개발자는 App을 사용하기를 원하고 채굴자는 고소득을 원하며 토큰 보유자는 가치상승을 원합니다. 각 유형의 참여자의 관삼사가 동일하지 않고 충돌이 자주 발생합니다. 예를 들어 App 사용량이 많아지면 트랜잭션 처리 수수료가 비쌉니다. (블록체인에 대한 수요가 증가함에 따라 더 비싸집니다) 비교적 가격 싼 거래는 채굴자에게 많은 수익을 창출하지 않으며 높은 가격인 토큰은 트랜잭션 비용에 기여하지 않습니다. (사용자가 지역 트랜잭션 수수료 설정을 조정하지 않으면 반대 상황이 발생합니다) 탈중앙화 컴퓨팅 플랫폼은 트랜잭션 처리를 통해 가치를 제공합니다. 그들의 토큰 가격은 네트워크의 본질적인 가치를 크게 변화시키지 않았습니다. 예를 들어 탈중앙화 컴퓨팅 플랫폼인 이더리움은 가격의 증가 또는 감소가 토큰의 본질적인 가치에 영향을 미치지 않습니다. 예를 들어 Gas price가 변경되지 않으면 사용자는 동일한 비용으로 네트워크에서 동일한 작업을 수행할 수 있습니다. 따라서 이더리움의 토큰 보유자는 적극적인 기여자가 아닌 투자자 역활을 수행하게 됩니다.

In the Nervos CKB, Store of Assets users want security of their assets; developers want more adoption, reflected in more assets preserved; miners want higher income and token holders want price appreciation of their tokens. Higher token price supports everyone’s objective — the network would be more secure, miners get higher income, and token holders get better return. Aligning all participants’ incentives allows the network to best harness network effects to grow its intrinsic value. It also produces a more cohesive community and makes the system less prune to governance challenges.

Nervos CKB에서 자산저장 사용자는 자산을 안전하게 보호하기를 원하며 개발자는 사용자에게 더 많은 App을 사용하길 원합니다. 더 많은 자산 가치 보존에 반영하며 채굴자는 소득을 높이고 토큰 소유자는 가치 상승을 원합니다. 가치가 올라가는 토큰은 모든 사람의 이익 및 네트워크의 안정성을 보장하며 채굴자 및 토큰 보유자는 더 좋은 인세티브를 받을 수 있습니다. 모든 참여자의 인센티브를 조정하여 네트워크가 네트워크 효과를 최대한 활용하여 본질적인 가치를 향상 시킬 수 있도록 합니다. 또한 시스템의 거버넌스 문제가 어려움 없이 밀접한 커뮤니티를 구축합니다.

### 7.3 네트워크 효과 및 네트워크 성장을 위한 가이드
As the network grows to secure more assets and common knowledge, more native tokens of the Nervos CKB are going to become occupied. This accrues value to the native tokens by reducing circulating supply and providing positive support to the market price of the tokens. The higher price and increased share of secondary issuance motivate miners to expand operations and make the network more secure, increasing the intrinsic value of the network and the native tokens, attracting more and higher value preservation usage.

네트워크가 더 많은 자산과 공통된 지식을 보호하기 위한 발전함에 따라 Nervos CKB 네이티브 토큰을 위한 공간을 더 많이 사용됩니다. 이는 네이티브 토큰에 대한 시장 가격 지원을 제공하면서 유동성 및 공급을 줄이고 CKB의 가치를 점차 누적할 것입니다. 토큰 가격이 올라가고 세컨드 발행이 늘어남에 따라 채굴자의 규모를 늘리면 네트워크의 안정성도 올라갑니다. 그 동시에 네트워크 및 네이티브 토큰의 내재 가치를 높이고 더 많은 가치저장을 창출할 수 있습니다.

The pro-cyclical loop of the network’s adoption and network’s intrinsic value provides a powerful growth engine for the network. Together with how the network’s value accrues to the native tokens and gets captured by long term holders, it makes the network’s native token an excellent candidate for store of value. Compared to Bitcoin as a monetary store of value, the Nervos CKB is similarly designed to be secure and long term decentralized. We believe Nervos CKB has a more balanced and sustainable economic model than Bitcoin, and also comes with intrinsic utility of securing crypto-assets and common knowledge.

네트워크가 사용하는 순방향 루프와 네트워크의 내재 가치는 강력한 성장 엔진을 제공합니다. 네트워크의 가치가 어떻게 성장이 누적되고 네이티브 토큰을 통해 어떻게 장기간 토큰 보유자를 참여할 수 있는가와 함께 이는 네트워크의 네이티브 토큰을 가치 저장을 위한 훌륭한 후보자가 됩니다. 비트코인의 화폐 가치 저장과 비교했을 때 Nervos CKB의 설계도 안정적이고 장기적인 탈중앙화를 구축했습니다. 우리는 Nervos CKB가 비트코인보다 균형 있고 지속 가능한 이코노미 모델을 가지고 있으며 암호화된 자산과 데이터를 보호할 수 있는 능력이 있다고 믿습니다.

### 7.4 ‘일급 자산’ 플랫폼의 개발자 비용
In Ethereum, the top level abstraction is its accounts. Assets are expressed as state owned by smart contract accounts. In the Nervos CKB, assets are the first class abstraction with cells, where ownership is expressed with the lock script of a transaction output, a concept known as “First-Class Assets”. In other words, just like Bitcoin, assets in the Common Knowledge Base are owned by users directly instead of being kept custody in a smart contract.

이더리움(Ethereum)에서 Top level의 추상적인것은 계정모델입니다. 스마트 계약 계정은 자산을 나타내는 상태를 가집니다. Nervos CKB에서 자산은 cell의 Top level의 추상화입니다. 소유권은 트랜잭션 출력에 대한 잠금 스크립트로 나타냅니다.( 일급자산이라는 개념입니다) 즉 비트코인 처럼 CKB의 자산은 스마트 계약이 아닌 사용자가 직접 소유합니다.

The “First Class Asset” design allows the state storage cost of owning assets put not on developers, but on individual users. For example, a developer could create a User Defined Token with 400 bytes of code as validation rules, and every record of asset ownership would take 64 bytes. Even if the assets were to have 10,000 owners, the developer would still only need to use 400 CK Bytes.

‘일급 자산’을 설계하면 개발자가 자산을 소유하지 않고 상태 저장 비용을 부담할 수 있지만 다른 독립 사용자가 부담할 수 있습니다. 예를 들어 개발자는 사용자 정의 토큰에 대해 400 CK Bytes의 코드를 사용하여 유효성 검증 규칙을 만들었으며 그 동시에 각 자산 소유권 기록을 64바이트를 사용했습니다. 자산 소유자가 10,000명인 경우에도 개발자는 여전히 400 CK Byte만 사용해야 합니다.

For developers, we expect the capital cost of building projects on the CKB is moderate even in a scenario that the price of the native tokens were to go up degrees of magnitude higher. For users, the cost of the 64 CK Bytes to own an asset on the Nervos CKB would also be trivial for a long time even in the most aggressive adoption assumption of the platform.

개발자는 네이티브 토큰의 가격이 크게 상승하더라도 CKB에서 프로젝트를 구축하는 데 드는 비용은 보통 수준이 될 것으로 예상됩니다. 사용자가 플랫폼에서 적극적으로 사용하는 가정하에 Nervos CKB에서 64 CK Bytes의 자산은 비용이 낮습니다.

In the future where those cost were to become meaningfully expensive, it’s always possible for developers to rely on lending to bootstrap their projects, and for users to move their assets off the Common Knowledge Base on to other transaction blockchains in the Nervos Network if they’re willing to take the corresponding trade-offs. Please see the “Nervos Network” section for more details.

미래에 이러한 개발비용이 많이 들게 되면 개발자는 계속 프로젝트 임대를 통해 프로젝트를 계속 진행할 수 있으며 만약 해당 거래를 수행할 경우 CKB 자산을 Nervos Network의 다른 트랜잭션 영역으로 이전할 수 있습니다. Nervos 네트워크에 관한 정보는 ‘7.6 Nervos Network’ 섹션을 참조하십시오.




### 7.5 자산 임대
Even Nervos CKB will support native token lending to improve the liquidity of the CK Bytes, thanks to the programming ability provided by CKB-VM and the Cell model. Since the utility of the native token is realized through possession instead of transactions, it’s possible to have risk-free un-collateralized lending for CK Bytes locked for known duration of time. Entrepreneurs can borrow the CK Bytes they need with much lower capital cost for a period such as 6 months to work on prototypes and prove their business model. Long term users can lend out their tokens to earn extra income.

실제로 Nervos CKB는 CKB-VM 및 Cell 모델에서 제공하는 프로그래밍 기능 덕분에 CK Bytes의 유동성을 향상하기 위해 네이티브 토큰의 기능은 트랜잭션이 아닌 공간점유로 수행되므로 알려진 시간 동안 무위험 무담보 대출을 위해 CK Byte를 락업 합니다. 개발자는 6개월 동안 프로토타입을 개발하기 위해 비즈니스 모델을 증명하여 임대비용을 낮추어 필요한 CK Byte를 빌려올 수 있습니다. 장기 토큰 보유자는 토큰을 빌려 추가 수입을 얻을 수 있습니다.

The effective interest rate of lending is determined by the market supply and demand, but the current state of token utilization also plays a big role. Higher utilization of the available global state means less tokens can be made available for lending. This makes the lending interest higher, and makes it more attractive to release state and lock tokens in the NervosDAO to earn income. This serves the purpose to help reduce the global state; lower utilization of the available state means more tokens can be lent out. This makes the lending interest rate lower to encourage adoption.

임대의 실제 이자율은 시장 공급 및 수요에 의해 결정되지만, 토큰의 점유율 또한 중요한 영향을 미칩니다. 전체 상태 이용률이 높으면 대출에 사용할 수 있는 토큰 수가 줄어듭니다. 이는 대출이자가 높아지며 Nervos DAO 계약에 락업된 토큰이자 보다 임대수입을 얻는데 매력적일 것입니다. 이는 전체 상태를 감소시키는 데 도움이 됩니다. 전체 상태 사용률이 낮아지면 더 많은 토큰을 임대할 수 있으며 대출 이자를 낮추어 임대를 장려합니다.

### 7.6 Nervos Network
The Nervos CKB is the base layer of the Nervos Network with the highest security, decentralization, transaction cost and state storage cost. Just like how Bitcoin and Ethereum could scale off-chain with lightening network and plasma solutions, Nervos CKB also embraces off-chain scaling solutions and allow users to preserve and transact assets off-chain. When using off-chain solutions, users and developers can choose their own trade-offs between cost, security, latency and liveness properties.

Nervos CKB는 최고 수준의 안정성, 탈중앙화, 트랜잭션 비용 및 상태 저장 비용으로 Nervos 네트워크의 베이스 레이어입니다. 비트코인과 이더리움이 확장성을 위해 lightening network와 plasma를 사용할 수 있는 것처럼 Nervos CKB는 오프체인 확장성 솔루션을 사용하여 사용자가 오프체인 자산을 저장하고 거래할 수 있습니다. 오프체인 솔루션을 사용할 때 사용자와 개발자는 비용, 안정성, 딜레이, 활성화간에 균형을 이룰 수 있습니다.

Owning and transacting assets on the Nervos CKB come with the highest capital and transaction cost, but is also the most secure. It’s best suited for high value assets and long term asset preservation; Layer 2 solutions can provide scaling for both transaction throughput and state storage, but they would come with either weakened security assumptions or mandate extra steps of repudiation, and often require participants to be online within a time window. If both are acceptable (likely for owning and transacting low value assets for short duration), the Nervos CKB can be used as security anchor to other transaction blockchains, to effectively magnify both its transaction and state storage capacities.

Nervos CKB에서 자산 및 거래 자산을 보유하려면 많은 자본 및 거래 비용을 지불해야 합니다. 또한 가장 안전한 방법이기도 합니다. 높은 가치 및 장기 자산 보유에 가장 적합합니다. 레이어 2 솔루션은 트랜잭션 처리링 및 상태 라이브러리를 확장할 수 있지만, 안정성이 문제가 되거나 강제적으로 추가 단계를 수행할 수 있으며 참가자가 특정 시간 동안 온라인 상태가 되도록 요구할 수 있습니다. Nervos CKB를 둘 다 받아들일 수 있다면(단기 소유권 및 낮은 액수의 자산 거래) Nervos CKB는 다른 거래 블록체인의 보안으로 사용되어 거래량 및 상태 라이브러리를 효과적으로 확장할 수 있습니다.

If operators of transaction blockchains don’t want to introduce extra security assumptions, they can mandate that high value assets to be issued on the CKB, and low value assets to be issued on transactional blockchains. Then they can use CK Bytes on the CKB to store periodic block commits, challenges and proofs from the transactional blockchains — critical common knowledge for secure off-chain transaction repudiation. If a transaction chain doesn’t mind introducing extra layer of security assumption with a committee-based consensus protocol, they could also have their validators bond CK Bytes on the CKB to explicitly adjust security parameters.

트랜잭션 블록체인 시스템이 추가 보안 증명을 도입하기를 원하지 않는다면 CKB 위에 높은 가치의 자산을 담보할 수 있고 트랜잭션 블록체인에서 낮은 가치 자산을 발행할 수 있습니다. 그런 다음 CKB에서 CK Byte를 사용하여 정기적인 블록 커밋을 저장합니다. 이는 트랜잭션 블록체인의 도전 및 증명이며 오프체인 트랜잭션의 안정성이 관건입니다. 트랜잭션 체인에 추가적인 보안 레이어를 도입하기 위해 위원회 기반의 합의 프로토콜을 사용해 신경 쓰지 않는 보안 노드를 관리하기 위해 CKB에 CK Byte를 바인딩하여 안전성 참수를 명확하게 제어할 수 있습니다.

## 8. 토큰 이코노미의 응용

The economic model of the Nervos CKB provides building blocks that application developers can use directly as part of their own economic model. We’ll list subscriptions and liquidity income as two such possible building blocks.
Subscriptions

Nervos CKB의 이코노미 모델은 App 개발자가 자신의 이코노미 모델의 일부분 직접 사용할 수 있는 모듈을 제공합니다. 구독 및 유동성 수익을 가능한 두 가지 모듈로 나열합니다.
구독모델

Recurring payment or subscription is a typical economic model for services offered on the blockchain that span over some duration of time. One such example is the off-chain transaction monitoring service that’s often needed for layer 2 solutions. On the Nervos CKB, duration based services can ask their users to lock certain amount of native tokens in the NervosDAO and designate the service providers as the beneficiaries of the generated interest income in a subscription based model. Users can stop using the services by withdrawing their tokens from the NervosDAO.

오랜 기간 동안 지불 또는 구독은 블록체인에서 서비스를 제공하는 전형적인 이코노미 모델입니다. 여기서는 레이어 2 솔루션에서 종종 오프라인 거래가 필요한 모니터링 서비스를 예로들 수 있습니다. Nervos CKB 기반 구독 모델을 기반으로 하는 특정 시간에 서비스는 사용자가 Nervos DAO에서 특정 수의 네이티브 토큰을 락업 하여 서비스 공급자는 이자 소득의 수혜자로 지정하도록 요구할 수 있습니다. 사용자는 Nervos DAO에서 토큰을 되돌리고 이러한 서비스 사용을 중단할 수 있습니다.

In fact, Store of Assets users that occupy global state can be seen as paying an ongoing subscription metered by the size of their state, and the beneficiaries are the miners that provide the security service.
Liquidity Income

실제로 전체 상태를 차지하는 자산보관 사용자는 상태 크기를 기반으로 지속적인 구독료를 지불하는 것으로 간주할 수 있으며 수혜자는 보안 서비스를 제공하는 채굴자입니다.

유동성 수익 모델

In a Plasma like layer 2 solution, a typical pattern is that users would deposit native tokens in a smart contract on the layer 1 blockchain in exchange for transaction tokens on the layer 2. A layer 2 operator with sufficient reputation can have users commit to fixed duration deposits, and then use such deposits to provide liquidity to the lending market and earn income. This gives operators of layer 2 solutions an additional revenue stream on top of the fees collected on layer 2.

Plasma와 같은 Layer 2 솔루션에서 일반적인 패턴은 레이어 1 블록체인의 스마트 계약에서 네이티브 토큰을 담보하여 레이어 2에 토큰으로 스왑합니다. 레이어 2는 사용자가 일정 기간 내에 담보의 정보를 제출한 다음 이러한 담보 자산을 대출로 사용하여 유동성을 제공하고 시장에 수익을 낼 수 있습니다. 이는 레이어 2 비용 청구에 추가하여 레이어 2 솔루션 운영자에게 추가 수익을 제공합니다.



## 부록1: 트랜잭션 비용 분석
Nervos CKB uses Proof of Work based Nakamoto consensus, similar to what's used in Bitcoin - for more details, please see the "Nervos Consensus Paper"

Nervos CKB는 Bitcoin에서 사용된 것과 유사한 작업증명(Proof of Work)기반의 나카모토 컨센서스를 사용합니다. 자세한 내용은 "Nervos Consensus Paper”를 참고 바랍니다. 
The economics of the consensus process is designed to incentivize nodes to participate in the consensus process and provide measurements that nodes can use to prioritize transactions. At the core, it's designed to help consensus nodes answer the question: "Is this transaction worth to be included in the next block if I had the opportunity to produce the block?"

컨센서스 프로세스의 경제성은 노드가 합의 프로세스에 참여하도록 유도하고 노드가 트랜잭션의 우선순위를 정할 때 사용할 수 있는 측정 값을 제공하도록 설계되었습니다. 핵심은 합의 된 노드가 "블록을 생성할 기회가 있다면, 이 거래가 다음 단계에 포함될 가치가 있는가?"라는 대답에 도움이 되도록 설계되었습니다.
A block producing node can do a cost/benefit analysis to answer this question. The benefit of including a transaction is to be able to collect its transaction fee, and the cost of including a transaction in a block has three parts:
Fee Estimation Cost ( ): this is the cost to estimate the maximum possible income if a node where to include a transaction
Transaction Verification Cost ( ): blocks containing invalid transactions will be rejected by the consensus process, therefore block producing nodes have to verify transactions before including them in a new block.
State Transition Cost (): after a block is produced, the block producing node has to perform local state transitions defined by state machines of the transactions in the block.

블록을 생성하는 노드는 위 질문에 대답하기 위해 비용/편익 분석을 수행할 수 있습니다. 거래를 포함하는 것의 이점은 트랜잭션 수수료를 회수 할 수 있고 블록에 거래를 포함하는 비용은 아래와 같은 세 부분으로 나뉩니다. : 
수수료 추정 비용 (Fee Estimation Cost :  ): 노드가 트랜잭션을 포함할 경우 가능한 최대 수입을 추정하는 비용입니다.
트랜잭션 검증 비용 (Transaction Verification Cost :  ): 잘못된 트랜잭션을 포함하는 블록은 합의 프로세스에 의해 거부되므로 노드를 생성하는 블록은 새로운 블록에 트랜잭션을 포함하기 전에 트랜잭션을 확인해야 합니다.
상태 이전 비용 (State Transition Cost : ): 블록이 생성된 후, 블록을 생성하는 노드는 블록 내 트랜잭션 상태머신에 의해 정의된 로컬 상태 이전을 수행해야 합니다. 

In particular, transaction verification,  has two possible steps:
: Authorization Verification Cost
: State Transition Verification Cost
특히, 트랜잭션 검증 비용  에는 두가지 가능한 단계가 있습니다. :
: Authorization Verification Cost : 인증검증비용 
: State Transition Verification Cost : 상태 전이 검증 비용

We use CPC and EVC to represent Complete Processing Cost and Estimation and Verification Cost:
CPC: Complete Processing Cost
EVC: Estimation and Verification Cost;

우리는 CPC 및 EVC를 사용하여 전체 처리 비용 및 추정 및 검증 비용을 나타냅니다. 
CPC: 전체 처리 비용

EVC: 추정 및 검증 비용


비트코인의 트랜잭션 비용 분석
Bitcoin allows flexible authorization verification with the Bitcoin Script. Users can script the authorization rules and build smart contracts throughwhen creating transactions. Bitcoin has a fixed state transition semantic, which is to spend and create new UTXOs. In Bitcoin, the result of the state transitions are already included in transactions, therefore the State Transition Cost (STC) is 0.
비트코인은 Bitcoin Script를 통해 인증확인을 수행합니다. 트랜잭션을 구축할 때 사용자는 scriptPubkey를 통해 권한 부여 규칙을 작성하여 스마트 계약을 작성할 수 있습니다. 비트코인은 UTXO 모델이라고 불리는 고정된 상태 전이를 가지고 있습니다. 우리는 새로운 UTXO를 소비하고 작성함으로써 상태 전이를 구현할 수 있습니다. 비트코인에서는 상태전이의 결과가 실제로 트랜잭션에 포함되었으므로 상태전이 비용(STC)은 0입니다.

Bitcoin uses the amount difference of the inputs and outputs to express transaction fees. Therefore, the cost of estimating transaction fees scales to  where  is the total number of inputs and outputs.
비트코인은 입력 및 출력 사이의 차이로 거래에 대한 트랜잭션 수수료를 나타냅니다. 따라서 수수료의 예상 비용은입니다. 그중 은 입력 및 출력의 총수량입니다.
Authorization verification in Bitcoin requires running scripts of all inputs. Because the Bitcoin Script prohibits JUMP/looping, the computation complexity can roughly scale to the length of the input scripts, as, where  is the number of inputs and  is the average script length of an input. Therefore, the total cost of  roughly scales to the size of total transaction.
비트코인 스크립트는 건너뛰기와 루핑을 금지하기 때문에 모든 입력 스크립트를 실해해야 하므로 입력의 수를 입력하여 각 입력 스크립트 길이 계산 복잡도를 예측할 수 있습니다. 따라서 전체 권한 검증 비용은 모든 트랜잭션의 크기로 대략 추정할 수 있습니다. 
Bitcoin's state transition rules are simple, and nodes only have to verify the total input amount is the same as the total output amount. Therefore, the  in Bitcoin is the same as , also scaling to .\
비트코인 상태변환에 대한 규칙은 매우 간단하며 노드는 총입력 수가 출력의 총 개수와 동일한지 획인해야 합니다. 따라서 비트코인의 상태변환와  확인 비용은 거의 동일합니다.
In total, Bitcoin's cost of processing a transaction roughly scales to the size of the transaction: 
요약하면 비트코인 처리 트랜잭션의 총 비용은 대략 트랜잭션 크기를 계산할 수 있습니다.


이더리움 트랜잭션 비용 분석
Ethereum comes with Turing-complete scriptability, and gives users more flexibility to customize state transition rules with smart contracts. Ethereum transactions include gaslimit and gasprice, and the transaction fees are calculated using the product of their multiplication. Therefore,  is .
이더리움은 튜링 완전 스크립트 작성 기능을 제공하며 사용자가 스마트 계약을 통해 상태 전이 규칙을 정의 할 수있는 유연성을 제공합니다. 이더리움 거래에는 가스 제한 및 가스 가격이 포함되며 거래 수수료는 곱셈의 곱을 사용하여 계산됩니다. 그러므로,  는 가 된다. 
Unlike Bitcoin, Ethereum's transactions only include the computation commands of state transitions, instead of the results of the state transitions. Therefore, Ethereum's transaction verification is limited to authorization verification, and doesn't have state transition verification. The rules of authorization verification in Ethereum are:

비트코인과 달리 이더리움의 거래에는 상태 전이의 결과 대신 상태 전이의 연산 명령만을 포함합니다. 따라서, 이더리움의 거래 검증은 승인 검증에 만 국한 되며 상태 전이 검증은 없습니다. 이더리움의 승인 검증 규칙은 다음과 같습니다. 
Verify the validility of the Secp256k1 signatures, with computation complexity of 
Verify the nonce match of the transaction and the account that starts the transaction, with computation complexity of 
Verify the account that starts transaction has enough ether to pay for the transaction fees and the amount transferred. This requires access to the account's current balance. Ignoring the global state size's impact on account access, we can assume the complexity of this step is also .
의 계산의 복잡성과 함께 Secp256k1 서명의 유효성을 확인하십시오. 
의 계산의 복잡성과 함께 거래를 시작하는 계정과 거래의 nonce와 일치 여부를 확인합니다. 
거래를 시작하는 계정에 거래 수수료와 이체 된 금액을 지불할 수 있는 충분한 이더리움이 있는지 확인하십시오. 이것은 계정의 현재 잔액에 대한 접근을 필요로 합니다. 계정 접근에 대한 전역 상태 크기의 영향을 무시하면서, 우리는 의  단계에 대한 복잡성도 가정할 수 있습니다. 
Based on the above, the overall authorization verification complexity in Ethereum is .
위의 내용을 기반으로, 이더리움의 전반적인 승인 검증의 복잡성은 입니다. 
Since every byte of the transaction data comes with cost , the larger  is, the more gas it needs, up to the gaslimit specified. Therefore,
거래 데이터의 모든 바이트는 비용 와 함께 제공되기 때문에, 가 클수록 가스 제한 까지 더 많은 가스가 필요하다. 그러므로,



Ethereum comes with a Turing complete VM, and the computation of the result state could include logic of any complexity. Ethereum transaction's  caps the upper bound of computation, therefore 。To summarize all the above:
이더리움에는 튜링완전 VM이 제공되며, 결과 상태 계산에는 모든 복잡성의 논리가 포함될 수 있습니다. 이더리움 트랜잭션의   은 계산 상한선을 초과하므로 가 됩니다. 위 모든 것을 요약하면 다음과 같습니다.




Different from Bitcoin,  for the Ethereum nodes is less than . This is because Ethereum nodes only compute the result state after transactions are included in the block. This is also the reason that transaction results on Ethereum could be invalid, (e.g. exceptions in contract invocation or the gas limit is exceeded), but the Bitcoin blockchain only has successfully executed transactions and valid results.

비트코인과 달리 이더리움 노드의 는 보다 작습니다. 이는 트랜잭션이 블록에 포함 된 후에만 이더리움 노드가 결과 상태를 계산하기 때문입니다. 이것은 또한 이더리움의 거래 결과가 무효가 될 수 있는 이유이기도 합니다. (예 : 계약 요청의 예외 또는 가스 한도 초과) 그러나 비트코인 블록체인은 트랜잭션과 유효한 결과만 성공적으로 실행했습니다.

Nervos CKB의 트랜잭션 비용 분석
Nervos CKB's transactions are structured with inputs and outputs, similar to Bitcoin's. Therefore, the  and  for the Nervos CKB are the same as those of Bitcoin's:
Nervos CKB의 트랜잭션은 비트코인과 유사하게 입력과 출력으로 구성됩니다. 따라서 Nervos CKB의 와 는 비트코인의 와 와 동일합니다.


Because CKB transactions include the result of the transactions as outputs, therefore:
CKB 트랜잭션은 트랜잭션 결과를 출력으로 포함하기 때문에 다음과 같습니다. :


계산상의 복잡성을 측정하는 Cycle
We introduce "cycle" as a unit of measurement for computation complexity in the CKB, similar to the "gas" concept in Ethereum. Nervos CKB's VM is a RISC-V CPU simulator, therefore cycles here refer to real CPU computation cycles in the VM. The cycle number for an instruction represents the relative computation cost of that instruction. Transactions in the Nervos CKB require the sender to specify the number of cycles required for its verification. Nodes can opt to set an acceptable cycle upper bound cyclemax, and only process transactions with fewer cycles. We'll also introduce cycles to a block, with its value equal to the sum of all specified transaction cycles. The value of cycles in a block can't exceed the value blockcyclesmax, which are set and can be automatically adjusted by the system.
우리는 이더리움의‘Gas’개념과 비슷한 CKB의 계산 복잡도 측정 기준으로 사이클을 소개합니다. Nervos CKB의 가상머신은 RISC-V CPU 에뮬레이터로 이는 참조되는 cycle은 실제로 가상머신에서 실제 CPU 작업의 계산주기입니다. 명령을 실행하는데 필요한 cycle 수는 명령의 상대적인 비용입니다. Nervos CKB의 트랜잭션은 보낸 사람이 확인할 필요가 있는 cycle 수를 지정해야하며 노드는 cycle수를 허용하는 상한 cycle max를 설정할 수 있으며 적은 수의 cycle를 필요하는 트랜잭션만 전송합니다. 또한 값이 지정된 모든 트랜잭션의 cycle 합계와 동일한 블록에 cycle를 도입할 것입니다.블록의 cycle값은 초기에 설정된 blockcyclemax 값을 초과할 수 없으며 시스템에서 자동으로 조정될 수 있습니다.
Nodes can set their cyclemax to different values. cyclemax only impacts how a block producing node accepts new transactions, not how a node accepts transactions in a new block. Therefore, it's not going to cause inconsistency in the validation of blocks. A valid block needs valid proof of work, and this cost discourages a block producing node to include an invalid transaction with high cycles value.
노드는 자신의 cycle max를 다른 값으로 설정할 수 있으며 cycle max는 현재 노드가 컨펌된 트랜잭션을 받아들이는지 여부에만 영향을 미치며 다른 노드는 새 블록에서 트랜잭션을 받아들이지 않아므로 블록컨펌의 유효가 불일치가 발생되지 않습니다. 유효한 블록은 작업량 증명의 유효한 증거가 필요하기 때문에 블록 생성 노드가 높은 cycle값을 갖고 유효하지 않은 트랜잭션을 포함하는 것을 방지합니다. 
The following table shows the runtime differences in Bitcoin, Ethereum and the Nervos CKB.
Nervos CKB의 차이점은 다음과 같습니다.

Here's a summary of the computational complexity of different parts of the consensus process for Bitcoin, Ethereum and Nervos CKB ( means cycle limit)
다음 표는 합의에 도달하는 과정에서 비트코인, 이더리움 및 Nervos CKB의 각 부분의 계산 복잡성을 요약한 것입니다. (cycle의 상한선 참조)

