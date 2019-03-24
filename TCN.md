# Nervos CKB 加密經濟模型提案 - 繁體中文翻譯(20190322)

> [此版本與最新版有部分差異，以原版為主](https://github.com/nervosnetwork/rfcs/blob/55ba3a38ed6d5ec028340af40b8c115add6ee897/rfcs/0015-ckb-cryptoeconomics/0015-ckb-cryptoeconomics.md)，歡迎各位提交 PR 一起修正這一份文件，讓中文讀者可以更容易閱讀這份白皮書。
>
> 如果你不熟悉 GitHub 的協作流程，請您先參考 [gitbeijing.com](http://gitbeijing.com/)，這裡有詳盡的解說，這個項目希望可以有你的參與，謝謝第一位 PR 貢獻者 Maple!!
>
> 謝謝 hujianping, Orangem21, mingrui, stwith 的貢獻，以及 Virale, u2, fuluwwa 參與討論，歡迎大家繼續提出你們的看法，love u guys!!

* * *

## 提案目錄結構

![Screenshot](https://github.com/hujianping/RFC-CN/blob/master/2D1FD8A824DC5A81BD6FF75B22C51AB1.png?raw=true)

## 1. 代幣經濟學的設計目標

Public permission-less blockchains are open and distributed systems with diverse groups of participants. A well designed crypto-economics model is to provide incentives so that participants’ pursuit of own economic interests leads to desired emergent behaviors in alignment with the protocol, to contribute to the blockchain network’s success.

More specifically, the design of a crypto-economic system has to provide answers to the following questions:

-   How can the economic model ensure the security of the protocol?
-   How can the economic model ensure long term sustainability of the protocol?
-   How can the economic model align the objectives of different actors to grow the value of the protocol network?

公有非許可鏈是開放給所有人自由參與的分散式系統。一個精心設計的加密經濟模型，可以將各方參與者的利益與協議的整體利益對齊, 使其在追求自身經濟利益的同時也能對整個區塊鏈網路做出貢獻。

更具體地說，加密經濟系統的設計必須回答以下問題：

-   經濟模型如何保障協議的安全性？
-   經濟模式如何維護協議的可持續性？
-   經濟模型如何將不同參與者的經濟目標與提高整個網路價值的目標對齊?

* * *

## 2. 比特幣的加密經濟模型

The Bitcoin protocol uses its native currency to incentivize miners to validate and produce blocks. The Nakamoto Consensus considers the longest chain as the valid chain, which encourages block producing miners to propagate new blocks as soon as they produce them, validate blocks as soon as they receive them to have the whole network achieve consensus on the global state.

The native tokens of the Bitcoin network function both as a utility token and an asset. When bitcoins function as a utility, they can be used to pay transaction fees; when they function as an asset, they can be used to preserve value over time. Those two use cases are often referred to as the “Medium of Exchange” (MoE) use case and the “Store of Value” (SoV) use case. The two use cases are not mutually exclusive. They are both important for the network to function. However, it’s important to study the economic motives of the users of both use cases as a guide to analyze the sustainability of the Bitcoin network.

The Bitcoin protocol constraints the network’s transaction throughput with a fixed block size. Users bid with fees on the limited throughput to have their transactions processed. With this auction like mechanism, transaction fees are determined by the transaction demand - the more demand there is on the network, the higher the transaction fee a user has to pay to beat the competition to have their transaction included.

比特幣協議使用原生代幣激勵礦工驗證交易和挖礦。Nakamoto 共識遵循最長鏈原則，以此激勵礦工在挖出新塊後立即廣播，在收到新塊後立即驗證，以達成全網共識。

比特幣的原生代幣既是功能代幣，也是儲值資產。當比特幣作為功能代幣時，可用於支付交易費用，當作為儲值資產時，可用來儲存價值。通常我們用術語 MoE (Medium of Exchange, 交易媒介) 和 SoV (Store of Value, 價值儲存)分別指代這兩種用途。MoE 和 SoV 的功能並不衝突，它們對比特幣網路的正常執行都發揮著重要的作用，研究這兩種用途的經濟動機對分析比特幣網路的可持續性具有重要的指導意義。

在比特幣協議中，對區塊大小的限制制約了整個網路的交易處理能力，使用者需要通過類似拍賣的機制競爭有限的交易處理資源。拍賣價格也就是交易費由實際的交易需求決定，當交易需求增加時，為了擊敗競拍對手，交易費的價格也會水漲船高。

* * *

### 2.1 比特幣作為交易媒介網路

The Medium of Exchange use case views the Bitcoin network primarily as a peer to peer value transfer network. MoE users don’t have to hold bitcoins to benefit from the network - it’s the transactions in themselves that provide value. In fact, there are specialized Bitcoin payment services to provide access to liquidity and allow senders and receivers to acquire and dispose of Bitcoins just in time to perform the value transfer, without having to hold the cryptocurrency. MoE users are not concerned with price, or the movement of price, but care about the fiat equivalent cost of the transaction fees.

It’s challenging for Bitcoin to become a dominant MoE network. If the protocol calibrates its block time and the block size, therefore fixing the supply of transactions, the success of the network will necessarily increase the cost of transactions, reducing its competitiveness among other similar purposed blockchains as well as its own forks; If the protocol aims to keep the transaction cost low and increase the supply of transactions with faster block time or bigger blocks, it could compromise both security and decentralization through higher fork rate and increased cost of consensus participation.

MoE 使用者將比特幣網路看作一個點對點的價值傳輸網路，他們不通過持有比特幣獲益，而是利用比特幣網路的點對點交易功能受益。事實上，已經有專業的比特幣支付服務商提供這種資金流動性服務，使用者不需要持有加密貨幣也可以將比特幣作為價值載體完成交易。MoE 使用者並不關心加密貨幣的價格和價格波動，他們只關心交易費用換算成法幣後的價格。

比特幣要成為一個 MoE 主導的網路是很有挑戰性的。如果協議限制了出塊時間和區塊大小，那麼網路的交易處理能力會非常受限，因此網路的繁榮必然會導致交易成本增加，而這將反過來降低網路的競爭力，這種情況也存在於其他類似的區塊鏈協議以及比特幣分叉鏈中。如果協議致力於維持較低的交易成本，通過設定更快的出塊時間或更大的區塊大小來提高交易處理能力，這會導致更頻繁的分叉或者更高的參與共識成本，實際上這相當於在去中心化與安全性上做了妥協。

* * *

### 2.2 比特幣作為價值儲存的網路

Store of Value users view the Bitcoin network as a protocol to provide security to its native cryptocurrency as an asset that can preserve value over time. They see the Medium of Exchange use case as the necessary function to go in and out of this asset. A store of value user, especially the ones who hold the cryptocurrency for a long time, doesn’t care much about the transaction cost, as they can amortize it over time. They do care about the value of a Bitcoin, which depends on the network’s security and decentralization - if the network becomes less secure and can be attacked easily, it’ll stop being perceived as a store of value and the tokens will lose value; if the network becomes centralized, Bitcoin as an asset no longer has independent value, but has to assume counter-party risk.

For Bitcoin to succeed as a SoV network, it has to continue to keep its monetary policy stable and its network secure and decentralized. However, Bitcoin’s monetary policy has a hard cap, and after all the coins are mined, the network can only pay for the miners with transaction fees. It’s still an open question whether this model could be sustainable, especially considering Store of Value networks themselves tend not to produce many transactions.

而 SoV 使用者則將比特幣網路看作一種為原生代幣提供安全保障的協議，他們相信原生代幣可以長期保值，而 MoE 是一種不可或缺的功能。SoV 使用者，特別是長期持幣者，並不在乎交易成本，因為交易成本會隨著持有時間的累積被攤薄。SoV 使用者關注的是比特幣本身的價值，而這依賴於網路的安全性和去中心化程度 - 如果網路不夠安全，攻擊很容易，那麼價值將無法被儲存，比特幣也將一文不值; 如果網路算力過於集中，比特幣作為一種資產不再具有獨立價值，並將面臨保管方風險。

如果比特幣要成為一個 SoV 主導的網路，其必須繼續堅持當前的貨幣政策，維護網路的安全性以及保持一定程度的去中心化。然而，比特幣的發行總量有限，當所有的比特幣被開採一空後，給礦工的激勵只剩下交易費。這種模式是否可持續仍然是一個問號，特別是在一個 SoV 主導的網路裡往往不會產生許多交易。

* * *

### 2.3 誰能長期補貼礦工？

Security and decentralization are two essential properties of a blockchain network, and they come with a high cost that has to be paid to the operators of the network. Bitcoin’s current model has network security entirely paid with transaction fees after all the coins are mined. However, the MoE users have very limited time exposure to the network’s security risk, therefore won’t be willing to pay for it; the SoV users have prolonged exposure to the network’s security risk and are willing to pay for it, but they produce nearly no transactions.

Bitcoin’s consensus mechanism incentivize miners to recognize the longest chain as the network’s canonical state. Miner’s ongoing supply of hashing power doesn’t only provide security for the current block, but the immutability of all the blocks before it on the canonical chain. Relying on the SoV users to make one time payments for the ongoing security protection they receive from miners is not sustainable.

In a SoV network, relying on inflation to fund network security is more incentive compatible with the users. Inflation based block reward mechanism represents indirect payment from the beneficiary of the network’s ongoing security to the provider of such security, in proportion to the duration that enjoy the service.

安全性和去中心化是區塊鏈網路的兩個基本屬性，維護這兩個屬性需要付出很高的成本，因此支付給網路維護者(主要是礦工)的獎勵必須能夠覆蓋這些成本。根據比特幣當前的模型，當代幣開採完畢後，如果礦工仍可賺取足夠的交易費，那麼比特幣網路依然保有安全性。然而， MoE 使用者需要承受網路安全風險的時間非常有限，因此他們不願意為此付費。而雖然 SoV 使用者願意支付高額交易費，因為他們暴露於網路安全風險的時間更長，但問題是他們很久才產生一次交易。

比特幣的共識機制激勵礦工去識別並驗證最長的鏈以當作全網的最新狀態。礦工持續投入的算力不只為最新的區塊提供了安全性，也維護了之前所有區塊的不可篡改性。僅靠 SoV 使用者的一次性付款讓礦工持續提供安全保障非長久之策。

而在 SoV 網路中，如果依靠通脹來為網路安全提供資金對礦工的激勵更持久，對使用者也更友好。基於通脹的區塊獎勵暗含使用者間接地向安全提供者支付費用，並且費用多少與其享受安全服務的時間成正比。

* * *

## 3. 可保值和交易的智慧合約平臺

Smart contract platforms like Ethereum come with Turing-complete programmability and can support a much wider variety of use cases. The native tokens are typically used to price and pay for the cost of decentralized computation. Like the Bitcoin network, smart contract platforms also have the dual functions of preserving value and performing transactions. They differ from the payment networks in that the value they preserve is not only their own native tokens, but also the internal states of decentralized applications, for example, crypto-assets ownership in ERC20 smart contracts.

像以太坊這樣的智慧合約平臺具有圖靈完備的可程式設計性，可以支援更多的應用場景。原生代幣通常用於為去中心化的計算服務定價和費用支付。與比特幣網路一樣，智慧合約平臺也具有資產保值和交易媒介的雙重功能。它們與純支付網路的不同之處在於，它們儲存的價值不僅僅是它們自己的原生代幣，還包括去中心化應用的內部狀態，例如在 ERC20 智慧合約裡的加密資產。

* * *

Another significant difference is that transactions on smart contract platforms are much more “portable”. It’s much easier to take advantage of the more advanced scripting capability of smart contract platforms, to develop interoperability protocols to move transactions to a more cost effective transactional blockchain and securely settle back to the main “system of record” blockchains.

另一個與支付網路的重大區別是智慧合約平臺上的交易更加「便攜」。利用智慧合約平臺更高階的指令碼優勢來開發互動協議，將交易轉移到更具成本效益的子鏈上，並安全地將資料取回主鏈，現在是更容易了。

* * *

The economic models of smart contract platforms face similar polarization tendency of payment networks - With their superior interoperable capabilities, smart contract platforms are going to be even more specialized into transactional platforms and preservation platforms. Economically, this bifurcation comes from the fact that the two use cases have different ways of utilizing system resources - transactions consume instantaneous but renewable computation and bandwidth resources, and preservation requires long term occupation of the global state. An economic model optimized for one is unlikely to be optimal for the other.

智慧合約平臺的經濟模型面臨著類似支付網路的兩極化趨勢 - 由於其良好的互動能力，智慧合約平臺要麼偏向「交易平臺」,要麼偏向「保值平臺」。在經濟上，這種分歧源自這樣的事實：這兩種「平臺」具有不同的系統資源利用方式，處理交易消耗的計算和頻寬是瞬時的，而且這兩種資源是可再生的，但是保值卻需要長期佔用全球共識狀態。為一個方向進行優化的經濟模型不太可能是另一個方向的最佳選擇。

* * *

Competitive transactional platforms need to prioritize for low transaction cost . Transactional users are willing to accept less-optimal security, because of their only moment-in-time, limited exposure to security risk. They’re willing to accept the possibility of censored transactions, as long as there are options to take their transactions elsewhere. A transactional platform that invests in either security or censorship resistance will have higher cost of transactions, reflected either with higher transaction fees or high capital cost for stakes in a “stake for access” model, making the network less competitive.

有競爭力的交易平臺需要優先考慮降低交易成本。MoE 使用者可以接受不太理想的安全性，因為他們只在有限的時間內暴露在危險之中。他們可以接受交易審查的可能性，大不了去其他地方進行交易。致力於提高安全性或抗審查性的交易平臺將付出更高的交易成本，這將導致更高的交易費或者在”stake for access”模型中付出更高的資金成本，這都會使得這個交易網路的競爭力下降。

* * *

This is especially true when a well designed inter-blockchain protocol can allow trust-less state transfers and fraud repudiation of transactions. We already can see examples of transactional users prioritizing cost over security in centralized crypto-asset exchanges and not-so-decentralized blockchains - despite their flaws, they’re still popular because of their transactional efficiency.

當設計良好的跨鏈協議可以允許無信任的狀態轉移與抗交易作惡時，這樣的狀況就更明顯了。我們已經可以看到很多的例子反映了 MoE 使用者會優先考慮低成本的手續費而不是更高的安全性，他們往往選擇在中心化的交易所和沒那麼去中心化的區塊鏈上交易。儘管這些網路環境存在安全缺陷，但由於交易效率的原因，它們仍然很受歡迎。

* * *

Competitive preservation platforms need to be sustainably secure and censorship resistant. It requires an economic model designed not around transactions that happen moment-in-time, but around the ongoing occupation of the global state, and have users pay for the network infrastructure metered in their consumption of this critical resource.

但是，有競爭力的保值平臺需要具有可持續的安全性和抗審查性。因此需要設計一種不是基於即時交易而是基於對世界狀態的佔用而設計的經濟模型，讓使用者為網路基礎設施的關鍵資源的消耗付費。

* * *

## 4. 資產儲存

One of the most important use cases for smart contract platforms is to issue tokens to represent ownership of assets. These crypto-assets can have their own communities and markets, and their values are independent from the value of their platform tokens. On the other hand, these assets depend on the platform to process transactions and provide security. Payment networks like Bitcoin can be seen as single asset platforms, where smart contract platforms are multi-asset platforms. Similar to the concept of “Store of Value” in the context of Bitcoin, we call the utility that smart contract platforms preserve the value of its crypto-assets “Store of Assets”.

Preservation focused smart contract platforms must have a Store of Assets token economics design. The level of platform security has to grow along with the asset value it preserves. Otherwise as asset value grows, it will be increasingly profitable to “double-spend” assets by attacking the consensus process of the platform.

智慧合約平臺最重要的用例之一是發行代幣來代表資產的所有權。這些加密資產可以擁有自己的社群和市場，其價值與平臺代幣的價值是獨立的。在另一方面，這些資產依賴於平臺來處理交易並提供安全性。像比特幣這樣的支付網路可以被視為單一資產平臺，而智慧合約平臺則是多資產平臺。與比特幣背景下的「價值儲存」概念類似，我們稱智慧合約平臺的功能是可以保留其加密資產「資產儲存」的價值。

以儲存資產為重點的智慧合約平臺，必須具有「資產儲存」的代幣經濟設計。平臺安全級別必須與平臺上加密資產的價值一起增長。否則隨著平臺上加密資產價值的增長，因為攻擊的利益會增長，平臺本身遭到「雙重花費攻擊」的可能性會大大增加。

* * *

None of the current smart contract platforms are designed as Store of Assets platforms. Their token economics are designed either to facilitate transactions (for example, Ethereum’s native tokens are to pay for the decentralized computation) or to fulfill staking requirements. In either case, the growth in asset value doesn’t necessarily raise miner’s income to provide more security.

Every multi-asset platform is an ecosystem of independent projects. The security of the platform can be seen as “public goods” that benefit all projects. To make the ecosystem sustainable from a security point of view, there has to be a clear mechanism that the platform captures the economic success of the ecosystem to raise its own level of security. In other words, a Store of Assets platform has to be able to translate the demand of crypto-assets to the revenue of its miners, often through raising the value of the native tokens that miners are compensated in.

目前的智慧合約平臺都不是為了「資產儲存」平臺而設計的。這些平臺的代幣經濟學旨在促進交易（例如，以太坊的原生代幣用於支付去中心化計算的費用）或滿足權益證明的要求。在任何一種情況下，資產價值的增長並不一定會提高礦工的收入，而事實是隻有確保礦工的持續高收入才能礦工持續投入，從而使得平臺獲得更多的安全保障。

每個多資產平臺都是獨立的生態系統。平臺的安全性可被視為有益於所有項目的「公用物品」。為了從安全的角度使得生態系統可持續發展，必須有一個明確的機制，即該平臺需要能夠捕捉到平臺上生態系統的成功，以同時提高其自身的安全水平。換句話說，「資產儲存」平臺必須能將對加密資產的需求轉化為其礦工的收入，通常是通過提高對礦工的補償，讓其獲得額外的原生代幣。

* * *

Otherwise, the platform’s level of security becomes the ceiling how valuable the assets can become. When the value of an asset rises such that typical transactions can no longer be sufficiently protected by the platform, the liquidity would dry up and demand on the asset will fade.

Decentralized multi-assets smart contract platforms have to be Store of Assets to be sustainable.

否則，平臺的安全水平會成為加密資產價值的上限。當資產價值上升，使得平臺不再能夠充分保護在平臺上的交易時，流動性就會枯竭，對資產的需求也會減少。

去中心化的多資產智慧合約平臺必須持續的做好「資產儲存」的功能。

* * *

## 5. 去中心化與狀態限制的需求

Like other long term store of value systems, a Store of Assets platform has to be neutral and free of risks of censorship and confiscation. These are the properties that made gold the world’s favorite the store of value for thousands of years. For open, permission-less blockchain networks, censorship resistance comes down to having the broadest consensus scope with a low barrier for consensus and full node participation. Comparing to payment networks, running a full node for a smart contract system is more resource intensive, therefore a Store of Assets platform has to take measures to protect the operating cost of full nodes to keep the network sufficiently decentralized.

與其他長期價值儲存的系統一樣，「資產儲存」平臺必須保持中立，並且沒有審查和充公的風險。這些條件使得黃金成為世界上數千年來最受歡迎的價值儲存。對於完全開放無須許可的區塊鏈網路，抗審查的能力主要來自於最廣泛的全球共識，並且讓全節點參與的門檻足夠的低。與支付網路相比，智慧合約平臺執行全節點需要更密集的資源，因此，「資產儲存」平臺必須採取措施來保持全節點的運營成本，以保持網路有足夠的去中心化。

* * *

Both Bitcoin and Ethereum throttle transaction throughput to make sure participation is not limited to only “super computers” - Bitcoin throttles on bandwidth and Ethereum throttles on computation. However, they haven’t taken effective measures to contain the ever growing global state necessary for consensus participation and independent transaction validation. This is especially a centralization force for high throughout smart contract platforms, where the global state grows even faster.

比特幣和以太坊都限制了交易吞吐量以確保參與方不僅只有「超級計算機」 - 比特幣限制頻寬，乙太網限制計算能力。然而，他們沒有采取有效的方式，來容納共識參與和交易驗證所需而且不斷增長的全局狀態。尤其是整個智慧合約平臺有著高度集中的需求，全局狀態的增長速度只會更快。

* * *

In Bitcoin, the global state is the UTXO set. Bitcoin doesn’t control the growth of the size of the UTXOs directly, but every new UTXO adds overhead to the transaction where it’s created, making the transaction more expensive.

在比特幣中，全局狀態是 UTXO 的集合。比特幣不會直接控制 UTXO 大小的增長，但每個新增的 UTXO 都會增加交易費用。

* * *

In Ethereum, the global state is represented with the EVM’s state trie, the data structure that contains the balances and internal states of all accounts. When new accounts or new contract values are created, the size of the global state expands. Ethereum charges fixed amounts of Gas for inserting new values into its state storage and offers fixed amounts of Gas as transaction refund when values are removed. Ethereum’s approach is a step in the right direction, but still has several issues:

-   the growth of the global state is not bounded in any way and can grow infinitely, therefore there’s no certainty in the cost of full node participation
-   the system raises one-time revenue for expanding the state storage, but miners and full nodes have to bear the expense of storage over time
-   there’s no obvious reason why the cost of expanding storage should be priced in fixed Gas amounts, which is used to price a unit of computation
-   the “pay once, occupy forever” state storage model gives very little incentive for users to voluntarily clear state and reduce the size of global state

在以太坊中，全局狀態由 EVM 的狀態樹來表示，該狀態是包含所有帳戶的餘額和內部狀態的資料結構。建立新帳戶或新的智慧合約值時，全局狀態的大小就會增加。以太坊收取固定的 Gas 費用用於存入新的資料，並在移除資料的時後提供固定數量的 Gas 作為交易退款。以太坊的方法是朝著正確方向邁出的一步，但仍有幾個問題：

-   全局狀態的增長不受任何限制，並且可以無限增長，因此全節點的參與成本並不確定
-   該系統為擴大狀態儲存提高了一次性收費，但礦工和全節點必須承擔長期儲存費用
-   沒有明顯的理由說明為什麼擴充套件儲存的成本應該以固定的 Gas 定價（Gas 用於定價一個計算單位的費用）
-   「一次性支付，永遠佔用」的狀態儲存模型的激勵很小，很難讓使用者自願清除狀態和減少全局狀態的佔用

* * *

The Ethereum community is actively working on this problem, and the leading solution is to charge smart contract “state rent” - contracts have to periodically pay fees based on the size of its state. If the rent is not paid, the contract goes to “hibernation” and not accessible before the payment is current again. We see several difficult-to-solve problems with this approach:

-   many contracts, especially popular ERC20 contracts, represent decentralized communities and express asset ownership of many users. It’s a difficult problem to coordinate all the users to pay for state rent in a fair and efficient way.
-   even a contract is current on its rent payment, it still may not be fully functional because some of its dependent contracts may be behind on their payments.
-   the user experience for contracts with state rent is sub-optimal

以太坊社群正在積極解決這個問題，領先的解決方案是收取智慧合約的「狀態租金」 - 合約必須根據其狀態佔用的大小來定期支付費用。如果沒有支付租金，合同將會進入「休眠狀態」，並且在支付租金之前無法訪問。我們看到這種方法有幾個難以解決的問題：

-   許多合約，特別是流行的 ERC20 合約，代表了分散的社群，並代表了許多使用者的資產所有權。協調所有使用者以公平並且有效率的方式支付租金是一個很難的問題。
-   即使一個合約的租金是已支付的狀態，它仍然可能無法運作順利，因為其他需要呼叫的合約可能還沒付款。
-   使用狀態租賃的合約是次等的使用者體驗。

* * *

We believe a well designed mechanism to regulate the state storage has to be able to achieve the following goals:

-   the growth of the global state has to be bounded to give predictability for full node participation. Ideally, the cost is well within the range of non-professional participants to keep the network maximally decentralized and censorship resistant.
-   with bounded growth of the global state, the price for expanding it and the rewards for reducing it should be determined by the market. In particular, it’s desirable to have the cost of expanding state storage higher when it’s mostly full, and lower when it’s mostly empty.
-   the system has to be able to continuously raise revenue from its state users to pay miners for providing this resource. This serves both purposes of balancing miner’s economics and providing incentives for users to clear unnecessary states sooner than later.

我們認為，一個精心設計的狀態儲存機制必須能夠實現以下目標：

-   必須限制全局狀態的增長，以便為參與全節點提供可預測性。理想情況下，成本能控制在非專業參與者可以負擔的範圍內，以保持網路最大程度的去中心化與抗審查。
-   隨著全局狀態的有限增長，價格的上升與降低將由市場決定。特別是當狀態儲存空間快滿的時後，需要將狀態儲存的成本提高，而當它大部分為空時，需要降低成本，這是非常吸引人的。
-   系統需要能夠不斷收取其狀態使用者的租金，以支付礦工提供這種資源。這有助於平衡礦工的經濟收入，同時讓使用者被激勵去清除不必要的狀態。

* * *

Just like how Bitcoin throttles and forces pricing on bandwidth, and Ethereum throttles and forces pricing on computation, to keep a blockchain network long term decentralized and sustainable, we have to come up with a way to constrain and price the global state. This is especially important for preservation focused, Store of Assets networks, where usage of the network is not about transactions that mostly happen off-chain, but the cost of ongoing occupation of the global state.

就像比特幣如何限制頻寬，以及以太坊限制計算的定價，來保持區塊鏈網路長期去中心化和可持續，我們必須提出一種對於全局狀態的約束與定價方法。對於以保護資產為重點的「資產儲存」平臺來說，這是特別重要的，因為這種平台關心的不是大部分將發生在鏈下的交易，而是持續佔用全局狀態的存儲成本。

* * *

## 6. Nervos CKB 的經濟模型

The Nervos Common Knowledge Base (Nervos CKB for short) is a preservation focused, “Store of Assets” blockchain. Architecturally, it’s designed to best support on-chain state and off-chain computation; economically, it’s designed to provide sustainable security and decentralization. Nervos CKB is the base layer of the overall Nervos Network.

Nervos Common Knowledge Base（簡稱 Nervos CKB）是一個以儲存價值為重點的「資產儲存」區塊鏈。在架構上，是為了要最好地支援鏈上的狀態和鏈外計算。在經濟上，是為了要提供可持續的安全性和去中心化。 Nervos CKB 是整個網路的基礎層。

* * *

### 6.1  原生代幣

The native token for the Nervos CKB is the “Common Knowledge Byte”, or “CK Byte” for short. The CK Bytes represent cell capacity in bytes and they give owners the ability to occupy a piece of the blockchain’s overall global state. For example, if Alice owns 1000 CK Bytes, she can create a cell with 1000 bytes in capacity, or multiple cells that add up to 1000 bytes in capacity. She can use the 1000 bytes to store assets, application state, or other types of common knowledge.

Nervos CKB 的原生代幣是 「Common Knowledge Byte」，簡稱「CK Byte」。 CK Byte 代表 Cell 空間，它們讓擁有者能夠佔用區塊鏈的全局狀態。例如，如果 Alice 擁有 1000 個 CK Byte，她可以建立一個空間為 1000 Byte 的 Cell，或者空間合計最多為 1000 Byte 的多個 Cell。她可以使用 1000 個 Byte 來儲存資產，App 狀態或是其他類型的資料資料。

* * *

A cell's occupied capacity could be equal to or less than its specified capacity. For example, for a 1000 byte cell, 4 bytes would be used to specify its own capacity, 64 bytes for the lock script and 128 bytes for storing state. Then the cell's current occupied capacity is 196 bytes, but with room to grow up to 1000 bytes.

 一個 Cell 佔用的空間應該等於或小於其指定空間。例如，對於一個 1000 Byte 的 Cell，使用 4 Bytes 來指定自己的空間，鎖定指令碼使用 64 Bytes，儲存狀態使用 128 Bytes。因此這個 Cell 實際佔用 196 Bytes，但是有充足的空間增長至 1000 Bytes。

* * *

### 6.2 代幣發行政策

There are two types of native token issuance. The “base issuance” has a finite total supply with a Bitcoin like issuance schedule - the number of base issuance halves approximately every 4 years until all the base issuance tokens are mined out. All base issuance tokens are rewarded to the miners as incentives to protect the network.

The “secondary issuance” is designed to collect state rent, and has issuance rate that’s constant over time. After base issuance stops, there will only be secondary issuance.

有兩種類型的原生代幣發行政策。 「基礎發行」的總供給量有限，發行時間表與比特幣類似 - 基本發行數量大約每 4 年減半一次，直到所有「基礎發行」的代幣被挖出來。所有「基礎發行」代幣都會獎勵給礦工，作為保護網路的激勵措施。

「二級發行」的設計則是為了收取狀態租金，每年的發行數量是不變的。「基礎發行」停止後，「二級發行」仍會繼續。

* * *

### 6.3 收取二級發行的狀態租金和 NervosDAO 設計

Since the native tokens represent right to expand the global state, the issuance policy of the natives tokens bounds the state growth. As state storage is bounded and becomes a scarce resource like bandwidth in Bitcoin and computation throughput in Ethereum, they can be market priced and traded. State rent adds the necessary time dimension to the fee structure of state storage occupation. Instead of mandating periodic rent payments, we use a two step approach as a “targeted inflation” scheme to collect this rent:

-   On top of the base issuance, we add the secondary issuance which can be seen as “inflation tax” to all existing token holders. For users who use their CK Bytes to store state, this recurring inflation tax is how they pay state rent to the miners.
-   However, we have also collected rent from the CK Bytes that are not used to store state, and we need to return to them what we collected. We allow those users to deposit and lock their native tokens into a special contract called the NervosDAO. The NervosDAO receives part of the “secondary issuance” to make up for the otherwise unfair dilution.

由於原生代幣代表了佔用全局狀態的權利，所以代幣發行政策會限制狀態的增長。由於狀態儲存受限制並且成為了稀缺資源，就好比比特幣的頻寬和以太坊的計算吞吐量，它們可以在市場上被定價和交易。狀態租金在狀態佔用的費用結構上，增加了必要的時間維度。我們採用兩個步驟作為「目標通脹」框架來收取這筆租金，而不是強制定期收取租金：

-   在「基礎發行」的基礎上，我們添加了「二次發行」，可以將其視為對所有代幣持有者的「通脹稅」。對於使用CK Byte 儲存狀態的使用者，這種定期的通脹稅是他們向礦工支付狀態租金的方式。
-   然而，由於我們對於那些沒有使用 CK Byte 儲存狀態的所有者也收取了租金，所以我們需要將租金歸還。我們允許這些使用者將他們的原生代幣存入並鎖定到一個特殊合約中，我們稱它為 NervosDAO。 NervosDAO 將接受部分「二級發行」的補償，以彌補因為不公平造成的稀釋。

* * *

Let's suppose at the time of a secondary issuance event, 60% of all CK Bytes are used to store state, 35% of all CK Bytes are deposited and locked in the NervosDAO, and 5% of all CK Bytes are kept liquid. Then 60% of the secondary issuance goes to the miners, 35% of the issuance goes to the NervosDAO to be distributed to the locked tokens proportionally. The use of the rest of the secondary issuance - in this example, 5% of the that issuance - is determined by the community through the governance mechanism. Before the community can reach agreement, this part of the secondary issuance is going to be burned.

假設在「二級發行」時，所有 CK Byte 的 60％ 用於儲存狀態，所有 CK Byte 的 35％ 被存放並鎖定在 NervosDAO 的合約中，剩下的 CK Byte 中的 5％ 保持流動性。那每次進行二級發行出塊獎勵的時候，60％ 的「二級發行」會獎勵給礦工，35％ 的會進入 NervosDAO 按比例分配給鎖定的代幣（使用者），最後剩下的 5％ 既沒有佔用也沒有鎖幣的部分是歸交治理機制處理；在治理沒有完善的方案前燒掉。

* * *

For long term token holders, as long as they lock their tokens in the NervosDAO, the inflationary effect of secondary issuance is only nominal. For them it’s as if the secondary issuance doesn’t exist and they’re holding hard-capped tokens like Bitcoin.

對於長期代幣的持有者，只要他們將代幣鎖定在 NervosDAO 合約中，「二次發行」的通脹效應只是名義上的。對他們而言，就像二次發行不存在一樣，他們持有的代幣，就會像比特幣這樣有硬頂的設計。

* * *

### 6.4 礦工補償

Miners are compensated with both block rewards and transaction fees. They receive all of the base issuance, and part of the secondary issuance. In the long term when base issuance stops, miners still receive state rent income that’s independent of transactions but tied to the adoption of the common knowledge base.

礦工會獲得兩種出塊獎勵和交易手續費。他們將會收到所有的「基本發行」，以及部分的「二級發行」。長期來看，當「基礎發行」停止後，礦工仍然可以獲得狀態租賃的收入。

* * *

### 6.5 交易手續費支付

A decentralized blockchain network’s transaction capacity is always limited and its resources are constrained. Transaction fees serve the dual purposes of establishing a market for the limited transaction capacity and as protection against spams. In Bitcoin, transaction fees are expressed with the difference between the outputs and inputs; In Ethereum, processing transactions requires miners to perform computations that can’t be estimated efficiently, therefore transaction fees are expressed as cost of unit of computation or as “gas price”. Ethereum transactions include both properties of “gas price” and “gas limit”, and the real transaction fee is  multiplied by amount of gas used, up to the specified .

去中心化區塊鏈網路的交易吞吐量是有限的，其資源是受到限制的。交易手續費有兩個目的，一個是為了有限的交易吞吐量建立一個市場，另一個則是防止惡意大量攻擊。在比特幣中，交易手續費表現在輸出和輸入之間的差異，而在以太坊中，處理交易需要礦工執行無法有效估算的計算，因此交易手續費表現為計算的單位成本或「gas price」。以太坊交易包括 gas price 和 gas limit 的屬性，實際交易費用是 gasPrice 乘以使用的 gas 量，但不會超過上限的 gasLimit。

* * *

To ensure decentralization, the Nervos CKB restricts both computation and bandwidth throughput, effectively making it an auction for users use those system resources. When submitting a transaction, the user can leave the total input cell capacities exceeding the total output cell capacities, leaving the difference as transaction fees expressed in the native tokens, payable to the miner that creates the block containing the transaction.

為了確保去中心化，Nervos CKB 限制了計算和頻寬的吞吐量，當用戶要使用這些系統資源時，它可以有效地成為一個拍賣市場。當用戶提交交易時，提交的總輸入需超過總輸出的 Cell，將其差值作為以原生代幣來支付的交易費用，支付給打包交易的出塊礦工。

* * *

The number of units of computation (called “cycles”) also needs to be submitted as part of the transaction. Nervos CKB is an “off-chain computation, on-chain verification” platform, therefore the cycles of computation are known by the client who submits the transaction. When producing blocks, miners order transactions based on both transaction fees and the number of computation cycles necessary for transaction validation, maximizing its per-computation-cycle income within the computation and bandwidth throughput restrictions.

計算的單位數量（計算迴圈數）也需要作為交易的一部分來提交。 Nervos CKB 是一種「鏈下計算，鏈上驗證」的平臺，因此提交交易的客戶端知道計算迴圈數。在出塊時，礦工根據交易費用和交易驗證所需的計算迴圈來制訂這個交易，最大化每一個計算迴圈數和頻寬吞吐量限制內的收入。

* * *

In the Nervos CKB, the transaction fees can be paid with the native tokens, user defined tokens or a combination of both.

在 Nervos CKB 中，可以使用原生代幣，或者「使用者自定義代幣」來支付交易手續費，而兩種的結合也可以用來支付手續費。

* * *

### 6.6 使用「使用者自定義代幣 UDT」支付交易手續費

Users are also free to user other tokens (for example, stable coins) to pay transactions fees, a concept known as “Economic Abstraction”. Note that even without explicit protocol support, it’s always possible to have users make arrangements with miners to pay transaction fees in other tokens outside of the protocol. This is often seen as a threat for many platforms - if the platform’s native tokens are purely to facilitate transactions, this would take away its intrinsic value and cause a collapse.

使用者還可以自由地發行其他代幣，例如穩定幣，用來支付交易費用，這個概念是一種「經濟抽象」。即使沒有明確的協議支援，使用者總是可以與礦工自行安排使用在協議之外的代幣支付交易手續費。這通常被許多平臺視為一種威脅 - 如果平臺的原生代幣純粹是為了促進交易，這將剝奪其系統的內在價值，並進一步導致崩潰。

* * *

With the Nervos CKB, we embrace economic abstraction and the benefits it brings. Since the intrinsic value of the native tokens is based not on transaction payment, economic abstraction doesn’t pose a threat to the stability of our economic model. We do expect, however, the native tokens themselves are going to be the payment method of choice for vast majority of users and use cases - the native tokens are going to the most widely held tokens in the Nervos ecosystem, and everyone who owns assets necessarily owns the Nervos natives tokens as state storage capacity that the assets occupy.

detailed analysis on transaction payments, please see Appendix 1.

通過 Nervos CKB，我們擁抱經濟抽象以及其帶來的好處。由於原生代幣的內在價值不是基於支付手續費的，因此經濟抽象不會讓我們的經濟模型造成威脅。然而，我們確實希望原生代幣將成為絕大多數使用者和應用的首選支付方式 - 原生代幣將會成為 Nervos 生態系統中最廣泛持有的代幣，因為每個擁有資產的人都必須擁有 Nervos 的原生代幣，原生代幣對應的是狀態的儲存空間，因為資產本身也佔有了一定的儲存空間。

更多的手續費分析詳見附件 1。

* * *

## 7. 用於儲存價值的經濟模型

The economic model of the Nervos CKB is designed specifically to preserve assets and other types of common knowledge. Let’s bring back the 3 high level design goals and examine our design in this context:

-   How can the economic model ensure the security of the protocol?
-   How can the economic model ensure long term sustainability of the protocol?
-   How can the economic model align the objectives of different actors to grow the value of the protocol network?

Nervos CKB 的經濟模型專門用於儲存資產價值和各種類型的資料。讓我們回顧 3 個重要的經濟模型設計目標，並在此背景下檢查我們的設計：

-   經濟模型如何確保協議的安全性？
-   經濟模式如何確保協議的長期可持續性？
-   經濟模型如何讓不同參與者擁有共同的目標，以促進整個網路的價值？

* * *

### 7.1 協議的安全性和可持續性

The main design choices we made to ensure security of the Nervos CKB as a “Store of Assets” protocol are:

-   Our native tokens represent claim to capacity in the state storage. This means the demand to holding assets on the platform directly puts demand on owning the native tokens. This creates an effective value capture mechanism into the native tokens from the assets they preserve. This is the only sustainable way that a “Store of Assets” platform can grow its security budget over time, instead of entirely basing it on speculation and altruism.
-   The secondary issuance makes sure miner compensation is predictable and based on preservation demand instead of transactional demand. It also eliminates potential incentive incompatibility of the Nakamoto Consensus nodes after block reward stops. The NervosDAO serves as the counter-force to the inflationary effects of secondary issuance, to ensure long term token holders are not diluted by this issuance.

我們為了確保 Nervos CKB 成為「資產儲存」協議並保證安全性而做出主要的設計選擇是：

-   我們的原生代幣代表了對狀態儲存的空間。這意味著如果想在平臺上持有資產，同時也要求擁有原生代幣。這代表了在平臺上持有資產等於創造了對原生代幣的需求，從而建立了一個有效的值捕獲機制到原生代幣中。這是「資產儲存」平臺隨著時間的推移，可以持續增加安全預算的唯一方式，而不是基於投機和利他主義。
-   二次發行確保對礦工的補償是可預測的，並且基於儲存價值的需求而不是可交易的需求。它還消除了出塊獎勵停止後如中本聰協議的共識節點，存在的激勵矛盾問題。 NervosDAO 是「二級發行」所導致通脹效應的反制力量，以確保長期持有代幣的人不會因為「二級發行」而被稀釋。

* * *

For a purpose of keeping the network decentralized and censorship resistant, we believe it’s important to limit the resource requirements of consensus and full nodes. We protect the operating cost of nodes by regulating the throughput of computation and bandwidth, similar to how it’s accomplished with Bitcoin and Ethereum. We regulate the state storage with a combination of a “cap and trade” pricing scheme and opportunity cost based cost model for storage users.

為了保持網路的去中心化和抗審查能力，我們認為降低參與共識以及成為主節點所需要的資源門檻是非常重要的。我們通過調節計算和頻寬的吞吐量來保護節點的運營成本，類似於比特幣和以太坊的實現方式。我們透過「總量管制」的定價框架，與基於儲存使用者的成本模型的機會成本這兩種方式，來管制了狀態儲存。

* * *

### 7.2 讓網路中每一類參與者的利益一致

In a typical smart contract platform, participants of the network have different interests - users want cheaper transactions, developers want adoption of their applications, miners want higher income, and holders want appreciation of their tokens. Those interests are not well aligned, and oftentimes in conflict - for example, more adoption won’t give cheaper transactions (they’ll be more expensive as more demand is put on the blockchain); cheaper transactions won’t give more income to the miners; higher token price won’t help with transaction cost (the opposite could happen if users don’t adjust their local transaction fee setting). Decentralized computation platforms provide value through processing transactions. The price of their tokens doesn’t materially change the intrinsic value of the network. For example, Ether’s price doubling doesn’t increase or decrease Ethereum’s intrinsic value as a decentralized computation platform. Assuming the gas price doesn’t change, a user can accomplish the same task with the same cost on the network. This makes token holders of Ethereum only take the role of an investor, instead of active contributors.

在典型的智慧合約平臺中，網路的參與者有不同的意圖 - 使用者希望更便宜的交易手續費，開發人員希望他們的 App 被使用，礦工希望獲得更高的收入，持有者希望他們的代幣增值。每一類的參與者的利益並不一樣，而且經常發生矛盾 - 例如，更多的 App 使用不會給予讓交易手續費更便宜（隨著對區塊鏈的需求增加，它們還會更加昂貴）；較便宜的交易不會給礦工帶來更多收入；較高的代幣價格將無助於交易成本（如果使用者不調整其本地交易費用設定，則可能發生相反的情況）。去中心化計算平臺通過處理交易提供價值。他們的代幣價格並沒有實質性地改變網路的內在價值。例如以太坊作為去中心計算平臺，價格的增加或減少並不會影響代幣的內在價值。假設 gasPrice 沒有變化，使用者可以在網路上以相同的成本完成相同的任務。這使得以太坊的代幣持有者只扮演了投資者的角色，而不是積極的貢獻者。

* * *

In the Nervos CKB, Store of Assets users want security of their assets; developers want more adoption, reflected in more assets preserved; miners want higher income and token holders want price appreciation of their tokens. Higher token price supports everyone’s objective - the network would be more secure, miners get higher income, and token holders get better return. Aligning all participants’ incentives allows the network to best harness network effects to grow its intrinsic value. It also produces a more cohesive community and makes the system less prune to governance challenges.

在 Nervos CKB 中，資產儲存使用者希望其資產安全；開發者希望 App 更多的被使用，反映在更多的資產價值儲存；礦工希望獲得更高的收入，而代幣持有者希望他們的代幣價格升值。更高的代幣價格支援每個人的利益 - 網路將更安全，礦工獲得更高的收入，並且代幣持有者獲得更好的回報。將所有參與者的激勵措施對齊，使網路能夠最好地利用網路效應來增強其內在價值。它還產生了一個更具凝聚力的社群，使得該系統面臨更少的治理挑戰。

* * *

### 7.3 引導網路效應和網路增長

As the network grows to secure more assets and common knowledge, more native tokens of the Nervos CKB are going to become occupied. This accrues value to the native tokens by reducing circulating supply and providing positive support to the market price of the tokens. The higher price and increased share of secondary issuance motivate miners to expand operations and make the network more secure, increasing the intrinsic value of the network and the native tokens, attracting more and higher value preservation usage.

隨著網路的發展得以保護更多的資產和共同知識，更多的 Nervos CKB 原生代幣所對應的空間將被佔用。這減少了流通量與供應量並同時提供原生代幣的市場價格支撐，將會逐漸累積 CKB 的價值。更高的代幣價格，以及增加的二次發行份額將可以激勵礦工擴大規模並使得網路更加安全，也同時增加了整個網路和原生代幣的內在價值，吸引更多和更高價值的資產儲存用例。

* * *

The pro-cyclical loop of the network’s adoption and network’s intrinsic value provides a powerful growth engine for the network. Together with how the network’s value accrues to the native tokens and gets captured by long term holders, it makes the network’s native token an excellent candidate for store of value. Compared to Bitcoin as a monetary store of value, the Nervos CKB is similarly designed to be secure and long term decentralized. We believe Nervos CKB has a more balanced and sustainable economic model than Bitcoin, and also comes with intrinsic utility of securing crypto-assets and common knowledge.

網路採用的順向迴圈和網路的內在價值為其本身提供了強大的增長引擎。連同網路如何逐漸累積價值，到原生代幣如何被長期持有者捕獲，都使得網路中的原生代幣成為價值儲存的絕佳候選者。與比特幣作為貨幣儲存價值相比，Nervos CKB 同樣設計為安全且長期去中心化的。我們認為 Nervos CKB 擁有比比特幣更加平衡和可持續的經濟模型，並且還具有保護加密資產及資料的功用。

* * *

### 7.4 開發者在「一級資產」平臺中的成本

In Ethereum, the top level abstraction is its accounts. Assets are expressed as state owned by smart contract accounts. In the Nervos CKB, assets are the first class abstraction with cells, where ownership is expressed with the lock script of a transaction output, a concept known as “First-Class Assets”. In other words, just like Bitcoin, assets in the Common Knowledge Base are owned by users directly instead of being kept custody in a smart contract.

在以太坊中，頂層的抽象是其帳戶。智慧合約賬戶擁有資產所代表的狀態。在 Nervos CKB 中，資產是 Cell 的頂層的抽象，其中所有權是交易輸出的鎖定指令碼來表示，這個概念稱為「第一級資產」。換句話說，就像比特幣一樣，CKB 中的資產由使用者直接擁有，而不是在智慧合約中被保管。

* * *

The “First Class Asset” design allows the state storage cost of owning assets put not on developers, but on individual users. For example, a developer could create a User Defined Token with 400 bytes of code as validation rules, and every record of asset ownership would take 64 bytes. Even if the assets were to have 10,000 owners, the developer would still only need to use 400 CK Bytes.

「第一級資產」的設計允許開發者可以不用擁有資產，以及負擔狀態儲存的成本，而是可以由其他獨立的使用者承擔。舉個例子，開發人員建立了一個使用者自定義代幣的驗證規則，使用了 400 CK Bytes 的程式碼，同時每個資產所有權的記錄都將佔用 64 個位元組。即使資產擁有 10,000 個所有者，開發人員仍然只需要使用 400 CK Bytes。

* * *

For developers, we expect the capital cost of building projects on the CKB is moderate even in a scenario that the price of the native tokens were to go up degrees of magnitude higher. For users, the cost of the 64 CK Bytes to own an asset on the Nervos CKB would also be trivial for a long time even in the most aggressive adoption assumption of the platform.

對於開發者而言，我們預計即使在原生代幣的價格上升幅度較大的情況下，在 CKB 上建設項目的成本也是適中的。對於使用者來說，即使平臺在被大幅度採用的假設下，64 CK Bytes 在 Nervos CKB 上的擁有成本也很低。

* * *

In the future where those cost were to become meaningfully expensive, it’s always possible for developers to rely on lending to bootstrap their projects, and for users to move their assets off the Common Knowledge Base on to other transaction blockchains in the Nervos Network if they’re willing to take the corresponding trade-offs. Please see the “Nervos Network” section for more details.

在未來這些開發成本變得非常昂貴的情況下，開發者仍然可以依靠租賃來繼續他們的項目，如果他們願意採取對應的取捨，使用者可以將他們的資產從 CKB 轉移到 Nervos Network 中的其他交易區塊鏈。相關資訊請參考「7.6 Nervos Network」部分。

* * *

### 7.5 租賃

Even Nervos CKB will support native token lending to improve the liquidity of the CK Bytes, thanks to the programming ability provided by CKB-VM and the Cell model. Since the utility of the native token is realized through possession instead of transactions, it’s possible to have risk-free un-collateralized lending for CK Bytes locked for known duration of time. Entrepreneurs can borrow the CK Bytes they need with much lower capital cost for a period such as 6 months to work on prototypes and prove their business model. Long term users can lend out their tokens to earn extra income.

實際上 Nervos CKB 也將支援原生代幣的租賃，以改善 CK Bytes 的流動性，這歸功於 CKB-VM 和 Cell 模型提供的程式設計能力。由於原生代幣的功能是通過空間佔用而不是交易來實現的，因此可以在已知的一定時間內鎖定 CK Bytes 進行無風險的無擔保借貸。開發者可以在 6 個月的時間內以較低的資金成本借入他們需要的 CK Bytes 來處理產品原型並證明他們的商業模式。長期的代幣持有者也可以出租他們的代幣來賺取額外收入。

* * *

The effective interest rate of lending is determined by the market supply and demand, but the current state of token utilization also plays a big role. Higher utilization of the available global state means less tokens can be made available for lending. This makes the lending interest higher, and makes it more attractive to release state and lock tokens in the NervosDAO to earn income. This serves the purpose to help reduce the global state; lower utilization of the available state means more tokens can be lent out. This makes the lending interest rate lower to encourage adoption.

租賃的實際利率由市場供求決定，但代幣的佔用狀況也有著重要的影響。如果全局狀態利用率高，代表可用於貸款的代幣就更少了。這將使得貸款利息更高，並且使得在 NervosDAO 合約中鎖定狀態，以獲得收入更具吸引力。這有助於減少全局狀態。而較低的全局狀態利用率代表著有更多的代幣可以出租。這將使得貸款利率降低以鼓勵使用。

* * *

### 7.6 Nervos Network

The Nervos CKB is the base layer of the Nervos Network with the highest security, decentralization, transaction cost and state storage cost. Just like how Bitcoin and Ethereum could scale off-chain with lightening network and plasma solutions, Nervos CKB also embraces off-chain scaling solutions and allow users to preserve and transact assets off-chain. When using off-chain solutions, users and developers can choose their own trade-offs between cost, security, latency and liveness properties.

Nervos CKB 是 Nervos Network 的基礎層，具有最高的安全性，去中心化，交易成本和狀態儲存成本。就像比特幣和以太坊可以通過 lightening network 和 plasma 來進行鏈下的擴容方案，Nervos CKB 也採用了鏈下擴容解決方案，並允許使用者在鏈下儲存和交易資產。當使用鏈下解決方案時，使用者和開發者可以在成本，安全性，延遲和活性之間做出權衡。

* * *

Owning and transacting assets on the Nervos CKB come with the highest capital and transaction cost, but is also the most secure. It’s best suited for high value assets and long term asset preservation; Layer 2 solutions can provide scaling for both transaction throughput and state storage, but they would come with either weakened security assumptions or mandate extra steps of repudiation, and often require participants to be online within a time window. If both are acceptable (likely for owning and transacting low value assets for short duration), the Nervos CKB can be used as security anchor to other transaction blockchains, to effectively magnify both its transaction and state storage capacities.

在 Nervos CKB 上擁有資產和交易資產需要最高的資本和交易成本，但也是最安全的。它最適合高價值資產和長期資產保值的用途。第 2 層解決方案可以為交易吞吐量和狀態儲存提供擴充套件，但它們會帶有較弱的安全性證明，或強制要求額外的步驟，而且通常會要求參與者在一定的時間範圍內線上。如果兩者都可以接受（可能用於短期擁有和交易低價值資產），Nervos CKB 可以被用作其他交易區塊鏈的安全之錨，以有效地放大其交易量和狀態儲存空間。

* * *

If operators of transaction blockchains don’t want to introduce extra security assumptions, they can mandate that high value assets to be issued on the CKB, and low value assets to be issued on transactional blockchains. Then they can use CK Bytes on the CKB to store periodic block commits, challenges and proofs from the transactional blockchains - critical common knowledge for secure off-chain transaction repudiation. If a transaction chain doesn’t mind introducing extra layer of security assumption with a committee-based consensus protocol, they could also have their validators bond CK Bytes on the CKB to explicitly adjust security parameters.

如果交易區塊鏈的系統不想引入額外的安全證明，他們可以在 CKB 上抵押高價值的資產，並在交易區塊鏈上發行低價值資產。然後，他們可以在 CKB 上使用 CK Bytes 來儲存週期性的區塊提交，這是交易區塊鏈的挑戰和證明 - 這是鏈下交易安全的關鍵常識。如果交易鏈不介意使用基於委員會的共識協議引入額外的安全性證明層，他們也可以讓他們的驗證節點在 CKB 上繫結 CK Bytes 以明確地調整安全的參數。

* * *

## 8. 代幣經濟學的應用

The economic model of the Nervos CKB provides building blocks that application developers can use directly as part of their own economic model. We’ll list subscriptions and liquidity income as two such possible building blocks.

Nervos CKB 的經濟模型提供了 app 開發人員可以直接使用的模組來作為他們自己的經濟模型的一部分。我們將訂閱和流動性收入列為兩個可能的模組。

* * *

-   Subscriptions

    Recurring payment or subscription is a typical economic model for services offered on the blockchain that span over some duration of time. One such example is the off-chain transaction monitoring service that’s often needed for layer 2 solutions. On the Nervos CKB, duration based services can ask their users to lock certain amount of native tokens in the NervosDAO and designate the service providers as the beneficiaries of the generated interest income in a subscription based model. Users can stop using the services by withdrawing their tokens from the NervosDAO.

    In fact, Store of Assets users that occupy global state can be seen as paying an ongoing subscription metered by the size of their state, and the beneficiaries are the miners that provide the security service.

-   訂閱模型

    很長一段時間，經常性支付或訂閱是區塊鏈上提供服務的典型經濟模型。這邊有一個例子是第 2 層解決方案經常需要離線交易的監控服務。基於 Nervos CKB 的訂閱模型上，基於一定時間內的服務可以要求其使用者在 NervosDAO 中鎖定一定數量的原生代幣，並將服務提供商指定為利息收入的受益者。使用者可以通過從 NervosDAO 撤回其代幣來停止使用這些服務。

    實際上，佔用全局狀態的資產儲存使用者可以被視為根據其狀態的規模支付持續訂閱的費用，受益人是提供安全服務的礦工。

* * *

-   Liquidity Income
    In a Plasma like layer 2 solution, a typical pattern is that users would deposit native tokens in a smart contract on the layer 1 blockchain in exchange for transaction tokens on the layer 2. A layer 2 operator with sufficient reputation can have users commit to fixed duration deposits, and then use such deposits to provide liquidity to the lending market and earn income. This gives operators of layer 2 solutions an additional revenue stream on top of the fees collected on layer 2.

-   流動性收入模型
    在類似於 Plasma 的第 2 層解決方案中，典型的模式是使用者將原生代幣抵押在第 1 層區塊鏈的智慧合約中以換取第 2 層上的交易代幣。具有足夠信譽的第 2 層運營商可以讓使用者提交固定時限內的抵押，然後使用這些抵押資產做為貸款，為市場提供流動性並賺取收入。這為第 2 層解決方案的運營商在第 2 層收取的費用之外，提供了額外的收入。

* * *

## 附件1 : 交易成本分析 | Appendix 1: Transaction Cost Analysis

Nervos CKB uses Proof of Work based Nakamoto consensus, similar to what's used in Bitcoin - for more details, please see the "Nervos Consensus Paper"

Nervos CKB採用的是基於中本聰共識的工作量證明（PoW）共識機制，這一點上類似於比特幣。欲瞭解更多關於Nervos CKB共識機制的細節，請參閱“Nervos Consensus Paper”。

* * *

The economics of the consensus process is designed to incentivize nodes to participate in the consensus process and provide measurements that nodes can use to prioritize transactions.  At the core, it's designed to help consensus nodes answer the question: "Is this transaction worth to be included in the next block if I had the opportunity to produce the block?"

在達成共識過程中的經濟學設計，旨在激勵所有參與共識達成的節點，並向節點提供可以用來確認事務優先順序的衡量標準。其核心內容，應該是幫助共識節點回答這樣一個問題：“如果我有機會生產下一個區塊，那麼這筆交易應不應該被加入這個區塊中。”

* * *

A block producing node can do a cost/benefit analysis to answer this question. The benefit of including a transaction is to be able to collect its transaction fee, and the cost of including a transaction in a block has three parts:

-   Fee Estimation Cost (![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/001.png) ): this is the cost to estimate the maximum possible income if a node where to include a transaction

-   Transaction Verification Cost (![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/002.png) ): blocks containing invalid transactions will be rejected by the consensus process, therefore block producing nodes have to verify transactions before including them in a new block.

-   State Transition Cost (![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/003.png)）: after a block is produced, the block producing node has to perform local state transitions defined by state machines of the transactions in the block.

為了回答這個問題，出塊節點可以進行一個成本/收益分析。節點在下一個塊中加入這筆交易能夠獲得的收益，就是這筆交易的轉賬手續費。而把這筆交易加入塊中需要付出的成本主要包含以下三個部分：

-   手續費估算成本(![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/001.png) )：這是節點在將未完成交易加入下一個塊的過程中，評估具體打包哪一筆未完成交易可以獲得最大收入的成本。

-   交易驗證成本(![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/002.png) )：如果塊中包含無效交易將在共識過程中被拒絕，因此出塊節點必須在把未完成交易加入新塊之前驗證每筆交易。

-   狀態轉換成本(![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/003.png))：在一個新塊生成後，出塊節點必須根據該區塊中包含的所有交易轉賬內容，通過狀態機完成本地狀態轉換。

* * *

In particular, transaction verification, ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/004.png)  has two possible steps:

-   ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/005.png): Authorization Verification Cost

-   ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/006.png): State Transition Verification Cost

特別的，在轉賬驗證中，![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/004.png) 可能包含以下兩個步驟：

-   ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/005.png):授權驗證成本

-   ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/006.png):狀態轉換驗證成本

* * *

We use CPC and EVC to represent Complete Processing Cost and Estimation and Verification Cost:

-   CPC: Complete Processing Cost

-   EVC: Estimation and Verification Cost;

我們採用CPC和EVC來表示全部處理成本和估算驗證成本：

-   CPC：完整處理成本

    -   ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/007.png)

-   EVC：估算及驗證成本
    -   ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/008.png)

* * *

### 比特幣的交易成本分析 | Bitcoin's Transaction Cost Analysis

Bitcoin allows flexible authorization verification with the Bitcoin Script. Users can script the authorization rules and build smart contracts through ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/009.png) when creating transactions. Bitcoin has a fixed state transition semantic, which is to spend and create new UTXOs. In Bitcoin, the result of the state transitions are already included in transactions, therefore the State Transition Cost (STC) is 0.

比特幣通過Bitcoin Script（比特幣指令碼）完成授權驗證。使用者在構建交易時可以通過scriptPubKey編寫授權規則，建立智慧合約。比特幣有固定的狀態轉換語句，也就是我們通常所說的UTXO模型，我們可以通過花費和建立新的UTXO來實現狀態轉換。在比特幣中，狀態轉換的結果其實已經被包含在交易中了，因此狀態轉換成本（STC）為0。

* * *

Bitcoin uses the amount difference of the inputs and outputs to express transaction fees. Therefore, the cost of estimating transaction fees scales to ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/010.png) where ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/011.png) is the total number of inputs and outputs.

比特幣通過輸入和輸出間的金額差異來表示該筆交易的交易手續費。因此手續費估算成本記為![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/010.png)，其中![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/011.png)是輸入和輸出總的數量。

* * *

Authorization verification in Bitcoin requires running scripts of all inputs. Because the Bitcoin Script prohibits JUMP/looping, the computation complexity can roughly scale to the length of the input scripts, as![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/012.gif), where ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/013.png) is the number of inputs and ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/014.gif) is the average script length of an input. Therefore, the total cost of ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/015.png) roughly scales to the size of total transaction.

比特幣的授權驗證需要執行所有輸入的指令碼，因為比特幣指令碼禁止跳過和迴圈，所以計算複雜度可以通過輸入指令碼的總長度![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/012.gif)進行估算，其中![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/013.png)是輸入的數量，![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/014.gif)是每個輸入的平均指令碼長度。因此總的授權驗證成本![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/015.png)可以粗略的通過全部交易的大小![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/012.gif)來進行估算。

* * *

Bitcoin's state transition rules are simple, and nodes only have to verify the total input amount is the same as the total output amount. Therefore, the ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/016.png) in Bitcoin is the same as ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/017.png), also scaling to ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/018.gif).

比特幣狀態轉換的規則十分簡單，節點只需要驗證輸入的總數是不是和輸出的總數相等即可。因此比特幣的狀態轉換驗證成本![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/016.png)和![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/017.png)一樣，約等於![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/018.gif)。

* * *

In total, Bitcoin's cost of processing a transaction roughly scales to the size of the transaction:
綜上，比特幣處理交易的總成本就可以通過交易大小去進行一個粗略計算：

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/019.png)

* * *

### 以太坊的交易成本分析 | Ethereum's Transaction Cost Analysis

Ethereum comes with Turing-complete scriptability, and gives users more flexibility to customize state transition rules with smart contracts. Ethereum transactions include _gaslimit_ and _gasprice_, and the transaction fees are calculated using the product of their multiplication. Therefore, ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/020.png) is ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/021.png).

以太坊具有圖靈完備的指令碼語言，允許使用者通過智慧合約自定義狀態轉換規則。以太坊的轉賬交易包括Gas Limit和Gas Price，交易手續費為這兩者的乘積。因此![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/020.png)等於![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/021.png)。

* * *

Unlike Bitcoin, Ethereum's transactions only include the computation commands of state transitions, instead of the results of the state transitions. Therefore, Ethereum's transaction verification is limited to authorization verification, and doesn't have state transition verification. The rules of authorization verification in Ethereum are:

-   Verify the validility of the Secp256k1 signatures, with computation complexity of ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/022.gif)
-   Verify the nonce match of the transaction and the account that starts the transaction, with computation complexity of ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/023.png)
-   Verify the account that starts transaction has enough ether to pay for the transaction fees and the amount transferred. This requires access to the account's current balance. Ignoring the global state size's impact on account access, we can assume the complexity of this step is also ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/023.png).

與比特幣不同，以太坊的轉賬交易只包括狀態轉換的計算命令，而不包含狀態轉換的結果。因此，以太坊的交易驗證僅限於授權驗證，而沒有狀態轉換驗證。以太坊的授權驗證規則如下：

-   驗證Secp256k1簽名的有效性，計算複雜度為![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/022.gif)，
-   驗證開啟交易的賬戶和交易之間的nonce是否一致，計算複雜度為![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/023.png)，
-   驗證啟動交易的賬戶是否有足夠的餘額支付轉帳手續費和轉帳金額。這需要訪問賬戶的當前餘額。忽略全局狀態大小對賬戶訪問的影響，我們可以假定這個步驟的複雜度也是![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/023.png)。

* * *

Based on the above, the overall authorization verification complexity in Ethereum is ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/024.gif).

綜上所述，以太坊中總的授權驗證複雜度為![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/024.gif)。

* * *

Since every byte of the transaction data comes with cost ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/025.png), the larger ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/026.png) is, the more gas it needs, up to the _gaslimit_ ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/027.png)specified. Therefore,

由於交易資料的每個位元組都有成本![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/025.png)，![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/026.png)越大，需要的gas也就越多，但是最多不超過Gas Limint![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/027.png)specified，因此：

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/54.png)

* * *

Ethereum comes with a Turing complete VM, and the computation of the result state could include logic of any complexity. Ethereum transaction's ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/028.png) caps the upper bound of computation, therefore ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/029.png)。To summarize all the above:

以太坊具備圖靈完備的虛擬機器，其狀態結果的計算可以包括任何複雜邏輯，以太坊交易中的Gas Limit成了計算進行的上限，因此![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/029.png)。綜上所述：

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/030.png)

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/031.png)

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/032.png)

* * *

Different from Bitcoin, ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/33.png) for the Ethereum nodes is less than ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/34.png). This is because Ethereum nodes only compute the result state after transactions are included in the block. This is also the reason that transaction results on Ethereum could be invalid, (e.g. exceptions in contract invocation or the gas limit is exceeded),  but the Bitcoin blockchain only has successfully executed transactions and valid results.

不同於比特幣，以太坊節點的![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/33.png)小於![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/34.png)。這是因為以太坊節點只在交易被包含在塊中之後才會計算狀態結果。這也是以太坊中交易結果可能無效的原因（比如會出現合約呼叫異常或者計算超出Gas Limit），而比特幣在出塊中就會執行轉帳過程並生成有效結果。

* * *

### Nervos CKB 的交易成本分析 | Nervos CKB's Transaction Cost Analysis

Nervos CKB's transactions are structured with inputs and outputs, similar to Bitcoin's. Therefore, the ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/35.png) and ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/36.png) for the Nervos CKB are the same as those of Bitcoin's:

Nervos CKB交易也是由輸入和輸出組成，類似於比特幣。因此Nervos CKB的![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/35.png)和![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/36.png)與比特幣相同：

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/37.png)

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/38.png)

Because CKB transactions include the result of the transactions as outputs, therefore:

因為在Nervos CKB交易的輸出中包含交易結果，因此：

![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/39.png)

* * *

### _cycles_ 作為計算複雜度的度量單位 | Cycles as Measurement Units of Computation Complexity

We introduce "cycle" as a unit of measurement for computation complexity in the CKB, similar to the "gas" concept in Ethereum. Nervos CKB's VM is a RISC-V CPU simulator, therefore cycles here refer to real CPU computation cycles in the VM. The cycle number for an instruction represents the relative computation cost of that instruction. Transactions in the Nervos CKB require the sender to specify the number of cycles required for its verification. Nodes can opt to set an acceptable cycle upper bound _cyclemax_, and only process transactions with fewer cycles. We'll also introduce _cycles_ to a block, with its value equal to the sum of all specified transaction cycles.  The value of _cycles_ in a block can't exceed the value _blockcyclesmax_, which are set and can be automatically adjusted by the system.

我們引入_cycles_ 作為CKB中計算複雜度的衡量單位，類似於以太坊中“Gas”的概念。Nervos CKB的虛擬機器是RISC-V CPU模擬器，這裡指的_cycles_ 其實就是虛擬機器中實際CPU工作的計算週期。執行一個指令的所需的_cycles_ 數量，就是該指令的相對計算成本。在Nervos CKB中的交易需要傳送方指定其所需要驗證的_cycles_ 數量，節點可以選擇設定接受_cycles_ 數量的上限_cyclemax_，進而只處理具有需要較少_cycles_ 運算的轉帳交易。我們還將在塊中引入_cycles_ ，其值等於所有指定事務的_cycles_ 總和。塊中_cycles_ 的值不能超過_blockcyclemax_的值，這些值已經被初始設定並且可以隨著系統自動調整。

* * *

Nodes can set their _cyclemax_ to different values. _cyclemax_ only impacts how a block producing node accepts new transactions, not how a node accepts transactions in a new block. Therefore, it's not going to cause inconsistency in the validation of blocks. A valid block needs valid proof of work, and this cost discourages a block producing node to include an invalid transaction with high _cycles_ value.

節點可以將其_cyclemax_設定為不同的值，_cyclemax_僅影響當前的出塊節點是否接受打包這筆交易，而不影響其他節點接受新塊中的交易，因此，它並不會導致區塊驗證的不一致。一個有效的塊需要有效的工作量證明，因此並不鼓勵出塊節點去接受一個具有很高_cycles_ 值，但是無效的轉帳交易。

* * *

The following table shows the runtime differences in Bitcoin, Ethereum and the Nervos CKB.

下表顯示了比特幣、以太坊和Nervos CKB在執行時的差異：

|          | Authorization (![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/40.png)） | State Validation (![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/41.png)) | State Transition（![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/42.png)） |
| -------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| Bitcoin  | Generalized                                                                                   | Fixed                                                                                            | None                                                                                            |
| Ethereum | Fixed                                                                                         | None                                                                                             | Generalized                                                                                     |
| CKB      | Generalized                                                                                   | Generalized                                                                                      | None                                                                                            |

* * *

Here's a summary of the computational complexity of different parts of the consensus process for Bitcoin, Ethereum and Nervos CKB (![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/55.png) means cycle limit)

下表是比特幣、以太坊和Nervos CKB在達成共識過程中不同部分的計算複雜性總結（![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/55.png)指_cycles_上限）

|          | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/43.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/44.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/45.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/46.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/47.png) |
| -------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Bitcoin  | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/48.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/49.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/50.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/49.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/49.png) |
| Ethereum | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/51.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/49.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/52.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/49.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/52.png) |
| CKB      | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/48.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/53.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/50.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/53.png) | ![](https://raw.githubusercontent.com/Jack0814/Picture/master/Img%202/53.png) |
