# Decentralized Identity System

The Decentralized Identity System is a collaboration between [District Labs](http://districtlabs.com/) and [Disco](https://disco.xyz/).

The proposed DID standard adheres to [progressive commitment threshold](https://hackmd.io/@kames/progressive-commitment-thresholds) engineering principles. Architected to gracefully help users progress through core Web3 commitment thresholds: **identity, finance and coordination**.

Starting as a decentralized identifier (DID) document and overtime evolving to become an user owned Smart Wallet, which inherits W3C [decentralized identifier](https://www.w3.org/TR/did-core/) and [verifiable credential](https://www.w3.org/TR/vc-data-model/) standards. 

The Public Key Infrastructure (PKI) smart contracts underpinning the Decentralized Identity System stack can also provide privacy preserving account recovery using zero-knowledge proofs. In other words, the DID document and accompanying Smart Wallet can be recovered either via a user's social network or through trusted third-party service providers. And is un-opinionated, from a technical perspective, as to what method a user chooses i.e. decentralized Web of Trust model or centralized Trust Anchor Gateway services. Rather it's only concern is exposing the primitives required for account recovery, and entirely the user has ultimate control in how they choose to utilize those account recovery primitives.

### Authors
- <img width="16px" src="https://github.com/decentralized-identity-system/did-dis/assets/3408362/ac5be9a7-69ea-4f40-b047-2501f961041d"> [Kames Geraghty](https://twitter.com/KamesGeraghty) - Founder & CTO of [District Labs](http://districtlabs.com/)
- <img width="16px" src="https://github.com/decentralized-identity-system/did-dis/assets/3408362/9df32c0d-7147-4ebb-a27b-3c4fcf9f2754"> [Evin McMullen](https://twitter.com/provenauthority) - Founder & CEO of [Disco](https://disco.xyz/)

# Overview

1. Introduction
    1. Where We're Coming From
    2. Where We Are Today
    3. Where We're Going
    4. Why Another DID standard?
3. Progressive Commitment Thresholds Principles
4. Architecture
    1. Cryptographically Enhanced API Service
    2. Offchain Data Storage
    3. Onchain Data Validation
6. Web2 Scalability & Web3 Security
7. Identity Hub - Offchain
8. Public Key Infrastructure - Onchain
9. Smart Wallet Creation
10. Conclusion

# Introduction

The Decentralized Identity System DID (`did:dis`) standard, proposed by [District Labs](http://districtlabs.com/) and [Disco](https://disco.xyz/), is an [Ethereum Virtual Machine](https://ethereum.org/en/developers/docs/evm/) (EVM) based decentralized identifier (DID) standard that embodies [progressive commitment threshold engineering principles](https://hackmd.io/@kames/progressive-commitment-thresholds).

The `did:dis` standard gives users a low-friction (and low-cost) method for bootstrapping a blockchain based Smart Wallet, with built-in support for the W3C [decentralized identifier](https://www.w3.org/TR/did-core/) and [verifiable credential](https://www.w3.org/TR/vc-data-model/) standards.

The standard relies on a combination of [counterfactual statements](https://en.wikipedia.org/wiki/Counterfactual_conditional), [offchain Identity Hubs](https://identity.foundation/decentralized-web-node/spec/0.0.1-predraft/) and [onchain Public Key Infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure).

Giving people all over the world the ability to bootstrap a new decentralized identifier using only **2 private key signatures**, while maintaining the ability to progressively strengthen the security and robustness of the underlying Smart Wallet, as they reach new Web3 commitment thresholds.

The standard uses the following concepts, standards and technologies:

- [Decentralized Identifier](https://www.w3.org/TR/did-core/#:~:text=Decentralized%20identifiers%20(DIDs)%20are%20a,the%20controller%20of%20the%20DID.) (DID) Documents
- Counterfactual Statements
- [Identity Hubs](https://identity.foundation/decentralized-web-node/spec/0.0.1-predraft) - Offchain Data Storage for Cryptographically Signed Messages
- Cross-Chain Interoperability Protocol ([EIP-3668](https://eips.ethereum.org/EIPS/eip-3668))
- Account Abstraction ([EIP-4337](https://eips.ethereum.org/EIPS/eip-4337) i.e. Smart Wallets)
- Onchain Public Key Infrastructure
- Authorization, Object Capabilities and Intents

### Where We're Coming From

In years previous uPort attempted to overcome decentralized identity challenges via the `did:uport` DID standard, which created a Smart Wallet on Ethereum mainnet.

Unfortunately, at the time we didn't have functioning L2 rollups, nor did we fully appreciate the power of counterfactual instantiation, and it's effectiveness in reducing onboarding friction.

The naive approach proved unworkable due to the costs associated with creating an onchain decentralized identifier, without even knowing if the user was ready to commit to the digital identity. Fortunately we did understand the power of delegating execution capabilities using meta-transactions -- which now underpins the ERC-4337 Account Abstraction standard.

Collectively we've learned a lot since those early days of blockchain based identities.

### Where We Stand Today

The `did:pkh` standard has since emerged as a more viable (technically scalable) option for onboarding users. Multiple applications and service providers use the `did:pkh` standard: Orbis, Gitcoin Passport, SpruceID, Disco, etc...

**A trade-off was made though.** The onboarding friction was reduced at the cost of long-term viability.

It was a fine trade-off to make. We needed to start somewhere and reducing friction was the number one priority for bootstrapping a new decentralized identity playground.

*But we have to continue evolving.* **We have to prepare for the future.**

### Where We Are Going

The `did:dis` standard attempts to overcome the limitations inherit in `did:pkh` (lack of an upgradable DID document) by engineering a decentralized identifier standard with progressive commitment thresholds. Starting as DID document and eventually evolving into a blockchained based Smart Wallet.

Prioritizing minimal onboarding friction and cost, while also retaining the ability create and update a DID document: authentications keys, object capabilities delegation, and invocation services. It does this by anchoring itslef to a public Ethereum virtual machine (EVM) blockchain, without requiring an onchain transaction to start.

The same principles found in Account Abstraction (counterfactual instantiation) can also be found in the `did:dis` standard.

At the core of account abstraction (EIP-4337) is the ability to deterministically predict a future smart contract address. Allowing third-parties to send assets (tokens, nfts, delegations, etc...) to that wallet, before a user has actually **materialized** the onchain Smart Wallet.

Applying those same principles, it's possible to counterfactually generate a user controlled DID document, that can also start receiving verifiable credentials and utilize the benefits of DID document. A user is able to gain these incredible benefits by anchoring to an future onchain Smart Wallet, but without actually an onchain transaction, until absolutely neccesary.

The `did:dis` DID standard is driven by the [progressive commitment threshold thesis](https://hackmd.io/@kames/progressive-commitment-thresholds). Taking a pragmatic approach to onboarding millions (and perhaps billions) of users into the world of Web3.

> “A scalable Web3 User onchaining strategy consists of 3 primary commitment thresholds: identity, finance and coordination.”

### Why Another DID standard?

Today the `did:key` and `did:pkh` DID standards offer the Web3 ecosystem a straight forward and reasonable approach to bootstrap a decentralized identity.

**However, they both have a major drawback -- the inability to manage a DID document.**

Users, companies and institutions can not be expected to use a single private key for the entire lifecycle of a digital identity. From a security perspective it’s a nightmare, and from a user experience perspective it’s unreasonable.

Standards like `did:web` offer us scalability and simplicity, but require users to anchor themselves to a "centralized" service for the entire lifecycle. The solution might work for companies and institutions, but it's an insufficient method for everyday users. Especially users that prioritize control and data sovereignty.

The `did:ion` standard, while arguably sufficiently decentralized, scalable, and supported by Microsoft, is unfortunately not forward looking enough. Anchoring itself to the Bitcoin network, it lacks the ability to take advantage of privacy preserving social recovery protocols made readily available through succinct zero-knowledge proofs, which are now becoming a foundational element in the EVM and Ethereum ecosystems.

- **did:pkh + did:key** - Instant setup with any wallet or key-pair, but can’t be upgraded overtime to meet the long-term demands of identity management i.e. no key rotation.
- **did:web** - Reliant on centralized DNS (domain name resolver) services for full life-cycle of a decentralized identity. Not viable for individual users.
- **did:ion** - Can’t easily utilize the benefits of a turing complete blockchain i.e. the Bitcoin blockchain dependency prevents taking advantage of features like social recovery using succinct zero-knowledge proofs, and a blockchain native public key infrastructure network with other advanced features.

**tl;dr:** Current DID standards are either too static, too centralized and/or too fragile.

**We need a better way forward.**

# Progressive Commitment Thresholds

We need a Decentralized Identity System that balances, scalablility, simplicity and sovereignty. Plus can interoperate with other cryptographic primitives, like Open Finance, inside a diverse and emergent Smart Wallet landscape.

> “A scalable Web3 User onchaining strategy consists of 3 primary commitment thresholds: identity, finance and coordination.”

[A Meta Strategy for Onchaining a Billion Users - Progressive Commitment Thresholds](https://hackmd.io/@kames/progressive-commitment-thresholds)

The Decentralized Identity System stacks helps users manage a DID document and a counterfactual Smart Wallet. And guides users gracefully through a complete Web3 journey.

**Meeting users where they are, instead of where we want them to be.**

# Architecture

The Decentralized Identity System stack is comprised of several Identity centric commitment thresholds:

1. Counterfactual Smart Wallet Setup (DID and Smart Wallet commitment signatures)
2. Updating the DID document (authorization keys, key agreements, object capabilities, etc...)
3. Optinal: Materialize Smart Wallet (onchain transaction to initialize smart contract)
4. Optional: Update offchain Identity Hub (change service providers)

In theory a user may never need to materialize the onchain Smart Wallet. 

For instance if a user never moves past the Identity threshold, steps 3 and 4 are optional. The DID will serve it's purpose as bridge into the world of Web3. And nothing more is required -- and that's O.K.

**The user gets ease of use, and ease of mind.**

Because, if for whatever reason, the user wants to change Identity Hub service providers, they can "materialize" the Smart Wallet and upgrade -- no problem. **The user is cryptographically in control every step of the way**. It's only when a major change is required, which usually indicates progressing past a specific commitment threshold, and it has accrued enough value, the counterfactual DID document can than be materialized as an onchain Smart Wallet. 

**tl:dr;** User avoids unnecessary friction, while still retaining full cryptographic controls.

## Cryptographically Enhanced API Services

Offchain Identity Hubs + Onchain Public Key Infrastructure = 🚀

During the initial stages of user onboarding the Decentralized Identity System stack can be thought of as a **cryptographically enhanced API service**.

Blurring the lines between **offchain** and **onchain** using private **Identity Hubs** and public **Public Key Infrastructure**.

The goal is to give users everything they need to bootstrap a new digital identity, while also give user's the ability to progressively decentralize and take ownership, as they self-actualize in their personal Web3 journey.

### How It Works

The Decentralized Identity System stack uses the [EIP-3668](https://eips.ethereum.org/EIPS/eip-3668) and [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337) standards to create a hybrid Smart Wallet that can handle both offchain Identity and onchain Finance primitives.

It purposefully dilineates offchain Identity and onchain Finance primitives for a reason.

**Identity and Finance have different security concerns.**

Which is why the DIS Smart Wallet intertwines the W3C [decentralized identifier](https://www.w3.org/TR/did-core/) and [verifiable credential](https://www.w3.org/TR/vc-data-model/) standards with the [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337) (Account Abstraction) specifications.

- Identity requires cryptographic guarantees like data authenticity and privacy preservation.
- Finance requires cryptographic guarantees like data finality and verification of shared global state.

Therefore we should treat Identity and Finance as unique primitives in the Web3 stack. 

**Interwoven, but seperate threads.**

Treating Identity and Finance as the same, and with the same cryptographic concerns is a mistake. And ultimately a disservice to future users of Web3.

The blockchain world is moving towards intents, object capabilities and other User focused abstractions. 

While Identity and Finance primitives will share more and more in common as the Web3 space matures, we should avoid treating them as the same and putting people's identities onchain. The convergance of these UX patterns can be observed simply by looking at MetaMask's [Delegatable framework](https://delegatable.org/) and taking note of how onchain access control pattern are aligning themselves with features that have been readily available in the decentralized identifier specifcations for many years.

The [Delegatable as An Intents Framework](https://hackmd.io/@kames/delegatable-intent-framework) article explores how object capabilities and intents are becoming first class citizens in the world of blockchain. And anyone deeply familiar with the DID document standards like object capabilities, will quickly realize these two systems (Identity and Finance) are reaching natural schelling points.

## EIP-3668 - Cross-Chain Interopability Standard
The EIP-3668 standard, proposed by [Nick Johnson](https://github.com/arachnid) founder of [Ethereum Name System](https://ens.domains/), is a clever mechanism for interweaving onchain and offchain (or cross-chain) data, like user signed messages or succinct zero-knowledge storage proofs.

> Contracts wishing to support lookup of data from external sources may, instead of returning the data directly, revert using OffchainLookup(address sender, string[] urls, bytes callData, bytes4 callbackFunction, bytes extraData). Clients supporting this specification then make an RPC call to a URL from urls, supplying callData, and getting back an opaque byte string response. Finally, clients call the function specified by callbackFunction on the contract, providing response and extraData. The contract can then decode and verify the returned data using an implementation-specific method.

```
┌──────┐                                          ┌────────┐ ┌───────────────────┐
│Client│                                          │Contract│ │Identity Hub @ url │
└──┬───┘                                          └───┬────┘ └──────┬────────────┘
   │                                                  │             │
   │ did(...)                                         │             │
   ├─────────────────────────────────────────────────►│             │
   │                                                  │             │
   │ revert OffchainData(sender, urls, callData,      │             │
   │                     callbackFunction, extraData) │             │
   │◄─────────────────────────────────────────────────┤             │
   │                                                  │             │
   │ HTTP request (sender, callData)                  │             │
   ├──────────────────────────────────────────────────┼────────────►│
   │                                                  │             │
   │ Response (result)                                │             │
   │◄─────────────────────────────────────────────────┼─────────────┤
   │                                                  │             │
   │ document(result, extraData)                      │             │
   ├─────────────────────────────────────────────────►│             │
   │                                                  │             │
   │ answer                                           │             │
   │◄─────────────────────────────────────────────────┤             │
   │                                                  │             │
```

The Decentralized Identity System stack takes advantage of this simple, yet powerful mechanism.

Resolving **offchain DID documents** through **onchain Public Key Infrastructure**.

Instead of requiring users to send a blockchain transaction when updating a DID document, which is a requirement in DID standards like `did:ethr` and previously `did:uport`, users can instead update a DID document offchain, via an Identity Hub. The onchain Public Key Infrastructure, which uses the EIP-3668 standard, can communicate with the offchain Identity Hub -- resolving a DID document using a decentralized and always available onchain API service. 

## EIP-4337 - Account Abstraction

The EIP-4337 standard, commonly referred to as Account Abstraction, also includes a clever mechanism, known as counterfactual instantiation. The Account Abstraction standard requires deterministic smart contract deployments, using low-level EVM instructions like the `CREATE2` opcode. 

The feature gives users the ability to "soft commit" to a future, not yet created smart contract.

> It is an important design goal of this proposal  (EIP-4337) to replicate the key property of EOAs that users do not need to perform some custom action or rely on an existing user to create their wallet; they can simply generate an address locally and immediately start accepting funds.

Simply put, when a user generates an EOA (externally owned account) private key, the user in effect automatically generates a counterfactual onchain Smart Wallet. The user simply need to commit to this future smart contract by signing an offchain commitments.

Example of a how to deterministically generate an account abstraction smart wallet.

```solidity=
function computeAddress(address entryPoint, address walletOwner, uint256 salt)
    public
    view
    override
    returns (address)
{
    return Create2.computeAddress(
        bytes32(salt),
        keccak256(abi.encodePacked(type(Wallet).creationCode, abi.encode(entryPoint, url, walletOwner)))
    );
}
```

## Decentralized Identier Document
The result of combining [EIP-3668](https://eips.ethereum.org/EIPS/eip-3668) and [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337) is a cost-effective, and thus scalable, method for creating/updating DID document via a countefactually created Smart Wallet i.e. soft commitments using cryptographically verifiable signatures.

The user's soft commitments are used to construct the `did:dis` decentralized identifier document.

Example of a  constructed`did:dis` identifier.

```json=
did:dis:10:0x1111111111111111111111111111111111111111:0x9999999999999999999999999999999999999999
```

- **CHAIN_ID** = 10
- **PKI** = 0x1111111111111111111111111111111111111111
- **Wallet** = 0x9999999999999999999999999999999999999999

The `CHAIN_ID` is used locate the `PKI` (public key infrastructure) smart contract, which in turn uses the `EIP-3668` standard to fetch a DID document via an offchain Identity Hub. The public key infrastructure smart contract verifies the offchain data; confirming the user's commitments to DID document and counterfactual Smart Wallet.

The `did:dis` DID standard is comprised of two core smart contracts:

- [Public Key Infrastructure (PKI)](https://github.com/district-labs/decentralized-identity-system/blob/main/contracts/did-dis-sol/contracts/PKI.sol)
- [Smart Wallet w/ offchain Identity and onchain Finance capabilities](https://github.com/district-labs/decentralized-identity-system/blob/main/contracts/did-dis-sol/contracts/Wallet.sol)

The `did:dis` standard adheres to the following format.

`did:dis:[CHAIN_ID]:[PKI]:[WALLET]`

- **CHAIN_ID:** EVM blockchain chainId.
- **PKI:** Public Key Infrastructure address.
- **WALLET:** Counterfactual Smart Wallet address.

The `did:dis` id is generated by appending the `CHAIN_ID`, `PKI` and `WALLET` fields together.

```
Example:
did:dis:10:0x1111111111111111111111111111111111111111:0x999999999999999999999999999999999999999
```

A user can present their decentralized identifier (DID) with anyone and that third-party can resolve the underlying DID document using an always available onchain public key infrastructure API service. Since we're using a public blockchain, all that's required is a blockchain identification (chainId) and public key infrastructure smart contract address. **And with that bit of information magic can happen.**

Example of a constructed `did:dis` document:

```jsonld=
{
  "@context": "https://w3id.org/did/v1",
  "id": "did:dis:10:0x1111111111111111111111111111111111111111:0x9999999999999999999999999999999999999999",
  "authentication": [{
    "id": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "type": "Secp256k1VerificationKey2018",
    "controller": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "publicKeyHex": "03aaab7a69bd3f8c27954afccc5c08f62418c6e2b7174773d2e99aa15477c9e8b7"
  }],
  "verificationMethod": [{
    "id": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "type": "Secp256k1VerificationKey2018",
    "controller": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "publicKeyHex": "03aaab7a69bd3f8c27954afccc5c08f62418c6e2b7174773d2e99aa15477c9e8b7"
  }],
  "service": [],
  "created": "2023-07-30T00:00:00Z",
  "updated": "2023-07-30T12:00:00Z"
}
```

The root EOA address (default Smart Wallet owner) is capable of signing offchain messages, is therefore included in the `authentication` and `verificationMethod` fields by default.

In the future, the DID document can be updated to include `authentication` and `verificationMethod` signing keys from a number of devices and services. For example a user controlled [PassKey](https://en.wikipedia.org/wiki/Passkey_(authentication)) or third-party managed JWT signing key can be added in a few simple steps. 

### Commitments using Signatures

Now that we've been equipped with a high-level understanding of the `did:dis` DID architecture, lets examine how the decentralized identifier document is created and verified using signature commitments.

Remember "counterfactual instantiation" from a few moments ago?

**Let's go back to that** -- specifically the `CREATE2` opcode.

```solidity=
function computeAddress(address walletOwner, uint256 salt) public view returns (address)
{
    return Create2.computeAddress(
        bytes32(salt),
        keccak256(
            abi.encodePacked(type(Wallet).creationCode, 
            abi.encode(ENTRYPOINT, address(this), walletOwner, urls)
        ))
    );
}
```

The `computeAddress` method takes 2 arguments:

- **walletOwner** - Owner of the smart wallet.
- **salt** - Randomness input

By default the `computeAddress` method includes the `ENTRYPOINT` constant, which is specific to the ERC-4337 standard, in the address computation step. That's because the Smart Wallet must be initialized with a reference to an ERC-4337 EntryPoint for UserOperations. That being said, the function can be upgraded to also accept the `ENTRYPOINT` constant as a function argument, if that approach is preferred.

What's important, is the user can sign Smart Wallet initialization arguments.

**And what can we do with that cryptographically signed message?**

We can ask users to "soft commit" to a future smart wallet by signing a hash of those arguments: `walletOwner` and `salt`.

```javascript
const signature = await wallet.signMessage(
    ethers.utils.arrayify(
        ethers.utils.solidityKeccak256(
            ["address", "address", "uint256"], 
            ['0x1111...1111', '0x9999...9999', 1]
        )
    )
);

// console.log(signature)
// 0x3e2982801c1869c3925238b9a31a10382838df553297ebebad271ff43c680d5a5d09227b5b60866a38915216a71da95de59cb2fc5850e49d71a70ee4207ab9161b
```

Resulting in a commitment to a future Smart Wallet and therefore also a `did:dis` DID document.

**Soft Commitment Signatures:**
- User commits to a future Smart Wallet by signing a hash of the transaction arguments, which are used to generate a future Smart Wallet.
- User commits to an DID document, containing the address of smart wallet, by signing a hash of the decentralized identifier document.

**Benefits of a Soft Commitment:**
- Create and upgrade a DID document with no overhead costs.
- Traditional "Web2" servers (Identity Hub) user to scale to millions of users.
- Users can "materialize" the Smart Wallet and switch offchain data storage providers.

## Offchain Data Storage Services 
As mentioned before, the `did:dis` standard is underpinned by the [EIP-3668](https://eips.ethereum.org/EIPS/eip-3668) standard.

The standard provides smart contracts with the ability to request offchain data.

**How?** By throwing a revert during a transaction read.

```
error OffchainLookup(
    address sender, 
    string[] urls, <- Reference to offchain data storage service providers.
    bytes callData, 
    bytes4 callbackFunction, 
    bytes extraData
)
```

The `string[] urls` field contains references to offchain data storage service providers i.e. Identity Hub.

The `urls` variable can include up to 4 unique API endpoints: either for redundancy with a single Identity Hub service provider, or to have redudancy by using multiple services providers via the same PKI router.

```solidity=
string[] public url = [
    // 🪩 Disco Identity Hub API 
    'http://hub-1.disco.xyz/counterfactual/{sender}',
    'http://hub-2.disco.xyz/counterfactual/{sender}',
    // 🌐 District Identity Hub API 
    'http://hub-1.districtlabs.com/counterfactual/{sender}',
    'http://hub-2.districtlabs.com/counterfactual/{sender}'
]

// Example of a minimal `PKI.did` method
function did(address entryPoint, address walletOwner, uint256 salt) external view {
    revert OffchainLookup(
        address(this),
        urls, // <- References offchain data storage providers
        abi.encodePacked(address(this));,
        this.document.selector,
        abi.encodePacked(entryPoint, walletOwner) // <- State passed back into the second contract call.
    );
}
```

### Identity Hubs

The `did:dis` standard relies on "traditional" offchain services to host data.

**Why?** Scalability and ease of use.

**The best part?** The data is still cryptographically verifiable.

In the Decentralized Identity System stack they're referred to as **[Identity Hubs](https://identity.foundation/decentralized-web-node/spec/0.0.1-predraft/)**.

Identity Hubs can range from incredibly simply to highly complex, depending on the service providers level of sophistication. Meaning the hub can act as stand-alone API to only resolve a DID document, or can be designed to provide more advanced Identity services, like verifiable credentials, selective disclosure, object capabilities, key agreement ceremonies, social recovery, etc...

The DIF Identity Hub (i.e. decentralized web node) specification includes references to IPFS as a storage provider, but unfortunately these systems haven't reached the maturity and scalability required to onboard millions of users in a reliable way. 

*Distributed and decentralized storage will play an important role in the future of Web3 Identity.* But unfortunately, it's not ready for mainstream adoption today. But that's O.K... because we can use cryptographically enhanced API services (private Identity Hubs) in the meantime.

# Web2 Scalability & Web3 Security
The Decentralized Identity System stack is pragmatic - balancing private Identity Hubs and public Public Key Infrastructure to provide low-friction and high-throughput, without compromising on user control and data sovereignty. It uses traditional "Web2 servers" to host and serve data, while relying on "Web3 blockchains" for routing, verification and hydration.

The DIS stack [first principles](https://en.wikipedia.org/wiki/First_principle) based approach to scaling Web3 Identity today.

**Prioritizing cryptographic guarantees like data authenticity and privacy preservation.**

It's not critical (at this point in time) if the infrastructure for storing data is decentralized or centralized. 

**What matters the most is cryptographically verifying data authenticity.** And driving mass adoption.

The **offchain Identity Hubs** and **onchain Public Key Infrastructure** architecture gives us the best of both worlds. We can rely on the high-throughput and stability of traditional offchain APIs, while also taking advantage of the built-in security and availability of onchain APIs.

**It's a win/win** -- Web3 Identity and Finance primitives are elegantly interwoven, while also reducing onboarding friction.

# Identity Hubs - Offchain
The role of an **Identity Hub** in the **Decentralized Identity System** is to act as a data storage layer for user signed data. 

When a user starts their Web3 journey this means a commitment to a DID document and future Smart Wallet. And in the future this might include anything from **verifiable credentials**, **object capabilities** and even **blockchain intents**.

*But again...* to start all we need are **signed commitments**.

**Identity Hubs don't need to be decentralized.**

Decentralizing an Identity Hub provides no significant advantages at this point in time. In fact providing a decentralized Identity Hub to users is likely a disadvantage this early in the user Web3 journey... *but that's another argument for another day.*

What we want -- **and need** -- is cryptographically provable commitment signatures.

We can work with commitment signatures. In fact, we can do a lot of interesting things with signatures.

## Crytographically Enhanced Data Storage
At a minimum an Identity Hub must resolve a DID document.

The [current prototype](https://github.com/district-labs/decentralized-identity-system/tree/main/apps/identity-hub-test-server) uses 5 pieces of data to achieve this:

- **DID** - Decentralized identifier document represented in object format.
- **HEX_DID** - Decentralized identifier document document in hex format.
- **SALT** - User (or application) supplied entropy.
- **SIG_WALLET** - User signature of a Smart Wallet initialization arguments
- **SIG_DID** - User signature of the stringified and hashed DID document

With this small set of data users can broadcast commitment to a DID and Smart Wallet.

People, organizations and institutions can use this commitment to form relationships. Relationships that are strengthened using identity primitives like verifiable credentials key agreement, selective disclosure, object capabilities, service invocations and more.

The [identity-hub-test-server](https://github.com/district-labs/decentralized-identity-system/tree/main/apps/identity-hub-test-server) demonstrates a minimal viable Identity Hub using a NodeJS Express server. The only responsibility of the hub is to serve data for the [PKI smart contracts](https://github.com/district-labs/decentralized-identity-system/tree/main/contracts/did-dis-sol) unit tests.


# Public Key Infastructure - Onchain
The first role of the onchain Public Key Infrastructure is to fetch, validate and hydrate DID documents.

The PKI smart contracts are in effect acting as a light-weight **trust anchor gateway**, with built-in security and availability guarantees. It's primary responsibility is to parse, verify and hydrate offchain data and act as cryptographically enhanced onchain API.

The [PKI smart contracts](https://github.com/district-labs/decentralized-identity-system/blob/main/contracts/did-dis-sol/contracts/PKI.sol) use the [EIP-3668](https://eips.ethereum.org/EIPS/eip-3668) standard. Which defines a simple mechanism for an onchain API to request data from an offchain API.

The `did` method on the `PKI` smart initializes a DID document resolution request. And the `document` and `resolve` methods handle the response from the offchain API, depending on if the Smart Wallet has been materialized or not.

-  **did** - Trigger fetch request
-  **document** - Consume fetch request if Smart Wallet is counterfactual
-  **resolve** - Consume fetch request if Smart Wallet is materialized

tl;dr The onchain Public Key Infrastructure resolves and verifies user signed commitments.

## Dispatch Request
The `did` method consumes a DID identifier.

```
did:dis:10:0x5FbDB2315678afecb367f032d93F642f64180aa3:0xF50C7Ce266d8F43cAF73a3307636E36C23090A7d
```

The identifier argument is parsed and injected as callback argument for the offchain API service.

Within the `did` function, the `pki` and `wallet` addresses are packed together as arguments for the Identity Hub. The arguments will also be returned as `callbackData` argument in the `document` and `resolve` methods. 


```solidity=
function did(string calldata id) external view {
        bytes memory callData = abi.encodePacked(address(this));
        address pki = _stringToAddress(id[11:53]);
        address wallet = _stringToAddress(id[54:96]);
        require(pki == address(this), "PKI: The DID document is not managed by this resolver");
        revert OffchainLookup(
            address(this),
            urls,
            callData,
            this.document.selector,
            abi.encodePacked(pki, wallet)
        );
    }
```


## Consume Responses
Once that Identity Hub has parsed and resolved the Public Key Infrastructure callback request, it will return a packed bytes argument, containing a salt, two commitment signatures and DID document as a packed bytes argument.

Here is an example of a basic Identity Hub implementation -- [available in the unit tests](https://github.com/district-labs/decentralized-identity-system/blob/main/contracts/did-dis-sol/test/PKI.test.ts).

```javascript=
const DID = {
    '@context': 'https://www.w3.org/ns/did/v1',
    id: "did:dis:10:0x5FbDB2315678afecb367f032d93F642f64180aa3:0xF50C7Ce266d8F43cAF73a3307636E36C23090A7d"
}
const SALT_DEFAULT = "1";
const SIG_WALLET = "0xab856af405d43f66dc003d335cec2889a4dfeb46b8dd2b9d9d1d4159f61b1ab32f4d5bb5bd51f05c9d1011b26d53408206fc2c4cf8adacd0d186ed125c5f430e1c"
const HEX_DID = ethers.utils.hexlify(ethers.utils.toUtf8Bytes(JSON.stringify(DID)));
const SIG_DID = "0xcc4d5855df6fae9b26d8fbdb18b0e8ecdb50c4bd7e13459ba7ad7fd2b500400c1befc3395bd7f0f6c6bbd129d0903924d2ad2d0809f1b42c0412bb5ede051cf01c"

// Offchain API for the onchain PKI smart contract.
app.post('/counterfactual/*', (req, res) => {
    const msg = ethers.utils.solidityPack(
        ['uint256', 'bytes', 'bytes', 'bytes'], 
        [BigNumber.from(SALT_DEFAULT), SIG_WALLET, SIG_DID, HEX_DID]
    );
    res.json({
        data: msg // <- Data passed to PKI `document` method as the `data` argument.
    });
})
```

The `document` and `resolve` methods on the [PKI smart contract](https://github.com/district-labs/decentralized-identity-system/blob/64812798ec3755082bbdf6ddd893039bdd0cba10/contracts/did-dis-sol/contracts/PKI.sol#L65) consumes the `data` field returned from the Identity Hub response. The `data` field from the Identity Hub is consumed as the onchain `data` argument. 

And the `callbackData` argument is the packed bytes initial `did` method callback request.


```solidity=
function document(
    bytes calldata data, // <- Passed by the offchain Identity Hub API service
    bytes calldata callbackData // <- Passed by the onchain PKI.did method
) external view virtual returns (string memory DID) {
    // Data from the `did` method callback
    bytes memory pki = callbackData[0:20];
    bytes memory wallet = callbackData[20:40];

    // Data from offchain Identity Hub
    // solidityPack(['uint256', 'bytes', 'bytes', 'bytes'], [BigNumber.from(SALT_DEFAULT), SIG_WALLET, SIG_DID, HEX_DID])
    bytes memory saltBytes = data[0:32];
    bytes memory didSignature = data[97:162];
    bytes memory walletSignature = data[32:97];
    bytes memory didHex = data[162:];

    // Hash the DID and the counterfactual Smart Wallet
    bytes32 didMsg = keccak256(abi.encodePacked(string(didHex)));
    address didSigner = _recoverSigner(didMsg, didSignature);
    
    // Hash the entry point, the DID signer (counterfactual smart wallet owner) and the salt.
    bytes32 walletMsg = keccak256(abi.encodePacked(pki, didSigner, saltBytes));

    // Recover the signer of the counterfactual Smart Wallet
    address walletSigner = _recoverSigner(walletMsg, walletSignature);

    // Check that the same signer signed both the DID and the counterfactual Smart Wallet
    address walletComputed = computeAddress(_bytesToAddress(entryPoint), didSigner, _bytesToUint256(saltBytes));
    require(walletComputed == _bytesToAddress(wallet), "INVALID WALLET ADDRESS");

    // Check that the signer of the Smart Wallet is the same as the signer of the DID
    require(walletSigner == didSigner, "INVALID SIGNATURE");
    return string(didHex);
}
```

The `document` and `resolve` method parse the response data, verifies authenticity and hydrating the DID document. Depending on whether the Smart Wallet is counterfactual or materialized will dictate which method is called and how the response is validated.

If everything passes validation the `didHex` bytes is returned as a stringified DID document.

```jsonld=
{
  "@context": "https://w3id.org/did/v1",
  "id": "did:dis:10:0x1111111111111111111111111111111111111111:0x9999999999999999999999999999999999999999",
  "authentication": [{
    "id": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "type": "Secp256k1VerificationKey2018",
    "controller": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "publicKeyHex": "03aaab7a69bd3f8c27954afccc5c08f62418c6e2b7174773d2e99aa15477c9e8b7"
  }],
  "verificationMethod": [{
    "id": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "type": "Secp256k1VerificationKey2018",
    "controller": "did:pkh:eip155:0x9999999999999999999999999999999999999999",
    "publicKeyHex": "03aaab7a69bd3f8c27954afccc5c08f62418c6e2b7174773d2e99aa15477c9e8b7"
  }],
  "service": [],
  "created": "2023-07-30T00:00:00Z",
  "updated": "2023-07-30T12:00:00Z"
}
```

# Smart Wallet Creation

Up until this point the user hasn't need to **materialize** their counterfactual Smart Wallet. 

**There wasn't a need.** Knowing a user committed to a future onchain smart wallet contract address was enough. The user was able to create a DID document referencing the counterfactual smart wallet i.e. **no onchain transaction required**.

But when the time is right, the user can materialize the smart wallet. And there might be a couple of reasons a user might want to materialize the Smart Wallet.

1. The user wants to progress in their Web3 journey into the financial commitment threshold.
2. The user wants to change to upgrade to a new offchain Identity Hub.

**We always want to be helping our users.**

In the beginning that probably means obfuscating implementation details. But as the user becomes more sophisticated, they will want more control over their digital identities.

**The Decentralized Identity System accounts for this need.** In fact it encourages user to progressively advance through multiple commitment thresholds. **It wants users to grow in sophistication and abilities**. If a user becomes more a sophisticated user of Web3, it means they can more meaningfully participate in other, more complex commitment thresholds: finance and coordination.

## Public Key Infrastructure & Smart Wallet Factory
The PKI smart contracts, in addition to resolving counterfactual DID documents, are also a factory for Smart Wallets.

> :warning: **Smart Wallet (Account Abstraction) features are missing from the current implementation.** For simplicities sake an existing EIP-4337 implementation will be forked and the DID standard will be integrated when the time is right.

To materialize a Smart Wallet, with built-in W3C DID support, the `deployWallet` method on the PKI smart contract is called using the EOA address and the salt used during the soft commitment ceremony.

```solidity=
// PKI.sol
function deployWallet(address walletOwner, uint256 salt)
    external
    override
    returns (Wallet)
{
    address walletAddress = computeAddress(walletOwner, salt);

    // Determine if a wallet is already deployed at this address, if so return that
    uint256 codeSize = walletAddress.code.length;
    if (codeSize > 0) {
        return Wallet(payable(walletAddress));
    } else {
        // Deploy the wallet
        // string[] memory __urls = new string[](1);
        // __urls[0] = urls[0];
        Wallet wallet = new Wallet{salt: bytes32(salt)}(ENTRYPOINT, address(this), walletOwner, urls);
        return wallet;
    }
}
```

Once a Smart Wallet is deployed the user will have the ability to update Identity Hubs.

```solidity=
// Wallet.sol
function setUrls(string[] memory __urls) external {
    // Clear existing URLs
    for (uint256 i = 0; i < _urls.length; i++) {
        delete _urls[i];
    }

    // Add new URLs
    for (uint256 i = 0; i < __urls.length; i++) {
        _urls.push(__urls[i]);
    }
}
```

**The user has choice.** 

They user can use the default offchain Identity Hubs provided by the Public Key Infrastructure or upgrade to a new service provider. It's entirely up to the user. The Decentralized Identity System simply provides reasonable defaults, until the user is ready to take over.

# Conclusion

The **Decentralized Identity System** embodies **progressive commitment threshold** principles.

Engineered for usability today and architected for upgradeability tomorrow.

The DIS stack focuses on meeting users where they, instead of where we want them to be. And is capable of evolving over time, **at the users disgression**, and when the time is right for them.

The Decentralized Identity System blurs the lines between offchain and onchain API services.

Taking the most desirable properties of Web2 (scalability) + Web3 (security) and interweaving them into a cryptographically enhanced data service. Allowing users, companies and institutions to establish a foothold in the world of decentralized and distributed systems, without unnecessary upfront costs and complexity.

**If the mission is onboarding 1,000,000's of people into Web3.**

Than the Decentralized Identity System is the foundation for making that happen.
