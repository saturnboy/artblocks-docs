---
sidebar_position: 2
title: Subgraph Entities
---

# Entities

- [`Project`](#project)
- [`ProjectScript`](#projectscript)
- [`ProposedArtistAddressesAndSplit`](#proposedartistaddressesandsplit)
- [`Contract`](#contract)
- [`Whitelisting`](#whitelisting)
- [`Account`](#account)
- [`AccountProject`](#accountproject)
- [`Token`](#token)
- [`MinterFilter`](#minterfilter)
- [`Minter`](#minter)
- [`ProjectMinterConfiguration`](#projectminterconfiguration)
- [`Payment`](#payment)
- [`Sale`](#sale)
- [`SaleLookupTable`](#salelookuptable)
- [`Transfer`](#transfer)
- [`ProjectExternalAssetDependency`](#projectexternalassetdependency)

# Project

Description: get various details about a specific project

| Field                                   | Type                                                               | Description                                                                                                                                        |
| --------------------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                                      | ID!                                                                | Unique identifier made up of contract address and project id                                                                                       |
| projectId                               | BigInt!                                                            | ID of the project on the contract                                                                                                                  |
| active                                  | Boolean!                                                           | Determines if the project should be visible to the public                                                                                          |
| additionalPayee                         | Bytes                                                              | Address to split primary sales with the artist                                                                                                     |
| additionalPayeePercentage               | BigInt                                                             | Percentage of artist's share of primary sales that goes to additional payee                                                                        |
| additionalPayeeSecondarySalesAddress    | Bytes                                                              | Address to split Secondary sales with the artist                                                                                                   |
| additionalPayeeSecondarySalesPercentage | BigInt                                                             | Percentage of artist's share of secondary sales that goes to additional payee                                                                      |
| artist                                  | Account!                                                           | Artist that created the project                                                                                                                    |
| artistAddress                           | Bytes!                                                             | Wallet address of the artist                                                                                                                       |
| artistName                              | String                                                             | Artist name                                                                                                                                        |
| baseIpfsUri                             | String                                                             | Uniform Resource Identifier Interplanetary File System (IPFS) of of a nonfungible token                                                            |
| baseUri                                 | String                                                             | The base URI is the mutual part among each NFT's URI. By default, the URI is baseURI/tokenId                                                       |
| complete                                | Boolean!                                                           | A project is complete when it has reached its maximum invocations                                                                                  |
| completedAt                             | BigInt                                                             | Timestamp at which a project was completed                                                                                                         |
| curationStatus                          | String                                                             | Curated, playground, factory. A project with no curation status is considered factory                                                              |
| currencyAddress                         | Bytes                                                              | ERC-20 contract address if the project is purchasable via ERC-20                                                                                   |
| currencySymbol                          | String                                                             | Currency symbol for ERC-20                                                                                                                         |
| description                             | String                                                             | Artist description of the project                                                                                                                  |
| dynamic                                 | Boolean!                                                           | Is the project dynamic or a static image                                                                                                           |
| invocations                             | BigInt!                                                            | Number of times the project has been invoked - number of tokens of the project                                                                     |
| ipfsHash                                | String                                                             | Interplanetary File System function that meets the encrypted demands needed to solve for a blockchain computation                                  |
| license                                 | String                                                             | License for the project                                                                                                                            |
| locked                                  | Boolean                                                            | For V3 and-on, this field is null, and projects lock 4 weeks after `completedAt`. Once the project is locked its script may never be updated again |
| maxInvocations                          | BigInt!                                                            | Maximum number of invocations allowed for the project                                                                                              |
| name                                    | String                                                             | Project name                                                                                                                                       |
| paused                                  | Boolean!                                                           | Purchases paused                                                                                                                                   |
| pricePerTokenInWei                      | BigInt!                                                            | Wei is the smallest denomination of ether—the cryptocurrency coin used on the Ethereum network. One ether = 1,000,000,000,000,000,000 wei (1018)   |
| royaltyPercentage                       | BigInt                                                             | Artist/additional payee royalty percentage                                                                                                         |
| script                                  | String                                                             | The full script composed of scripts                                                                                                                |
| scripts                                 | [`Project!`](#project)                                             | Parts of the project script                                                                                                                        |
| scriptCount                             | BigInt!                                                            | The number of scripts stored on-chain                                                                                                              |
| externalAssetDependencyCount            | BigInt!                                                            | The number of external asset dependencies stored on-chain                                                                                          |
| externalAssetDependenciesLocked         | Boolean!                                                           | Once the project's external asset dependencies are locked they may never be modified again                                                         |
| scriptJSON                              | String                                                             | Extra information about the script and rendering options                                                                                           |
| scriptTypeAndVersion                    | String                                                             | Script type and version (see `scriptJSON` if null)                                                                                                 |
| aspectRatio                             | String                                                             | Aspect ratio of the project (see `scriptJSON` if null)                                                                                             |
| tokens                                  | [`Token!`](#token)                                                 | Tokens of the project                                                                                                                              |
| useHashString                           | Boolean!                                                           | Does the project actually use the hash string                                                                                                      |
| useIpfs                                 | Boolean                                                            | Does the project use media from ipfs                                                                                                               |
| website                                 | String                                                             | Artist or project website                                                                                                                          |
| proposedArtistAddressesAndSplits        | ProposedArtistAddressesAndSplit                                    | Proposed Artist addresses and payment split percentages                                                                                            |
| owners                                  | [AccountProject!](#accountproject)                                 | Accounts that own tokens of the project                                                                                                            |
| createdAt                               | BigInt!                                                            | When project inititated                                                                                                                            |
| updatedAt                               | BigInt!                                                            | When project updated                                                                                                                               |
| activatedAt                             | BigInt                                                             | WHen project activated                                                                                                                             |
| scriptUpdatedAt                         | BigInt                                                             | when the script was updated                                                                                                                        |
| contract                                | Contract!                                                          | Contract associated to project                                                                                                                     |
| minterConfiguration                     | ProjectMinterConfiguration                                         | Minter configuration for this project (not implemented prior to minter filters)                                                                    |
| saleLookupTables                        | [SaleLookupTable!](#salelookuptable)                               | Lookup table to get the Sale history of the project                                                                                                |
| externalAssetDependencies               | [ProjectExternalAssetDependency!](#projectexternalassetdependency) | Projects external asset dependencies                                                                                                               |

# ProjectScript

Description: get specific details of the project script

| Field   | Type     | Description                                                  |
| ------- | -------- | ------------------------------------------------------------ |
| id      | ID!      | Unique identifier made up of contract address and project id |
| index   | BigInt!  | The dependency index                                         |
| project | Project! | Name of project                                              |
| script  | String!  | Script of the project                                        |

# ProposedArtistAddressesAndSplit

Description: get specific details on the pay flow for a specified artist

| Field                                   | Type     | Description                                                       |
| --------------------------------------- | -------- | ----------------------------------------------------------------- |
| id                                      | ID!      | Unique identifier made up of contract address and project id      |
| artistAddress                           | Bytes!   | Proposed artist address                                           |
| additionalPayeePrimarySalesAddress      | Bytes!   | Proposed artist additional payee address for primary sales        |
| additionalPayeePrimarySalesPercentage   | BigInt!  | Proposed artist additional payee percentage for primary sales     |
| additionalPayeeSecondarySalesAddress    | Bytes!   | Proposed artist additional payee address for secondary sales      |
| additionalPayeeSecondarySalesPercentage | BigInt!  | Proposed artist additional payee percentage for secondary sales   |
| project                                 | Project! | Project associated with this proposed artist addresses and splits |
| createdAt                               | BigInt!  | When address initiated                                            |

# Contract

Description: get specific information about contracts

| Field                               | Type                           | Description                                                                                                                     |
| ----------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| id                                  | ID!                            | Unique identifier made up of contract address                                                                                   |
| type                                | CoreType!                      | Core contract type                                                                                                              |
| renderProviderAddress               | Bytes!                         | Address that receives primary sales platform fees                                                                               |
| renderProviderPercentage            | BigInt!                        | Percentage of primary sales allocated to the platform                                                                           |
| renderProviderSecondarySalesAddress | Bytes                          | Address that receives secondary sales platform royalties (null for pre-V3 contracts, check Royalty Registry)                    |
| renderProviderSecondarySalesBPS     | BigInt                         | Basis points of secondary sales allocated to the platform (null for pre-V3 contracts, check Royalty Registry)                   |
| mintWhitelisted                     | [Bytes!]!                      | List of contracts that are allowed to mint                                                                                      |
| randomizerContract                  | Bytes                          | Randomizer contract used to generate token hashes                                                                               |
| curationRegistry                    | Bytes                          | Curation registry contract address                                                                                              |
| dependencyRegistry                  | Bytes                          | Dependency registry contract address                                                                                            |
| nextProjectId                       | BigInt!                        | Project ID listed on the contract                                                                                               |
| projects                            | [Project!](#project)           | List of projects on the contract                                                                                                |
| tokens                              | [Token!](#token)               | List of tokens on the contract                                                                                                  |
| whitelisted                         | [Whitelisting!](#whitelisting) | Accounts whitelisted on the contract                                                                                            |
| createdAt                           | BigInt!                        | When contract initiated                                                                                                         |
| updatedAt                           | BigInt!                        | When contract updated                                                                                                           |
| minterFilter                        | MinterFilter                   | Associated minter filter (if applicable)                                                                                        |
| preferredIPFSGateway                | String                         | The Engine Flex contract allows you to specify preferred gateways for the currently supported dependency types (IPFS & Arweave) |
| preferredArweaveGateway             | String                         | The Engine Flex contract allows you to specify preferred gateways for the currently supported dependency types (IPFS & Arweave) |
| newProjectsForbidden                | Boolean!                       | New projects forbidden (can only be true on V3+ contracts)                                                                      |

# Whitelisting

Description: get whitelist information

| Field    | Type      | Description                            |
| -------- | --------- | -------------------------------------- |
| id       | ID!       | Unique identifier whitelist account id |
| account  | Account!  | Account associated to whitelisting     |
| contract | Contract! | contract associated to whitelisting    |

# Account

Description: get specific information about an account

| Field           | Type                               | Description                                  |
| --------------- | ---------------------------------- | -------------------------------------------- |
| id              | ID!                                | Unique identifier account id                 |
| tokens          | [Token!](#token)                   | Tokens the account has                       |
| projectsOwned   | [AccountProject!](#accountproject) | Projects the account owns tokens from        |
| projectsCreated | [Project!](#project)               | Projects the account is listed as artist for |
| whitelistedOn   | [Whitelisting!](#whitelisting)     | Contracts the account is whitelisted on      |

# AccountProject

Description: get project account information

| Field   | Type     | Description                    |
| ------- | -------- | ------------------------------ |
| id      | ID!      | Unique identifier token id     |
| account | Account! | Account asssociated to project |
| project | Project! | Name of project                |
| count   | Int!     | Total count of the project     |

# Token

Description: get various token information

| Field            | Type                                 | Description                                                                                  |
| ---------------- | ------------------------------------ | -------------------------------------------------------------------------------------------- |
| id               | ID!                                  | Unique identifier made up of contract address and token id                                   |
| tokenId          | BigInt!                              | ID of the token on the contract                                                              |
| contract         | Contract!                            | Contract the token is on                                                                     |
| invocation       | BigInt!                              | Invocation number of the project                                                             |
| hash             | Bytes!                               | Unique string used as input to the tokens project script                                     |
| owner            | Account!                             | Current owner of the token                                                                   |
| project          | Project!                             | Project of the token                                                                         |
| uri              | String                               | Specifies the endpoint for retrieving access tokens when OAuth 2.0 authentication is enabled |
| createdAt        | BigInt!                              | When token initiated                                                                         |
| updatedAt        | BigInt!                              | When token updated                                                                           |
| transactionHash  | Bytes!                               | Transaction hash of token mint                                                               |
| transfers        | [Transfer!](#transfer)               | Transfers of the token                                                                       |
| saleLookupTables | [SaleLookupTable!](#salelookuptable) | Lookup table to get the Sale history                                                         |
| nextSaleId       | BigInt!                              | Next available sale id                                                                       |

# MinterFilter

Description: get details about minters on a project

| Field             | Type               | Description                                          |
| ----------------- | ------------------ | ---------------------------------------------------- |
| id                | ID!                | Unique identifier made up of minter contract address |
| coreContract      | Contract!          | Associated core contract                             |
| minterAllowlist   | [Minter!]!         | Minters allowlisted on MinterFilter                  |
| associatedMinters | [Minter!](#minter) | Minters associated with MinterFilter                 |
| updatedAt         | BigInt!            | When minter updated                                  |

# Minter

Description: get details about mint on a project

| Field                         | Type          | Description                                                              |
| ----------------------------- | ------------- | ------------------------------------------------------------------------ |
| id                            | ID!           | Unique identifier made up of minter contract address                     |
| type                          | MinterType!   | Minter type                                                              |
| minterFilter                  | MinterFilter! | Associated Minter Filter                                                 |
| minimumAuctionLengthInSeconds | BigInt        | Minimum allowed auction length in seconds (linear Dutch auction minters) |
| minimumHalfLifeInSeconds      | BigInt        | Minimum allowed half life in seconds (exponential Dutch auction minters) |
| maximumHalfLifeInSeconds      | BigInt        | Maximum allowed half life in seconds (exponential Dutch auction minters) |
| extraMinterDetails            | String!       | Configuration details used by specific minters (json string)             |
| coreContract                  | Contract!     | Associated core contract                                                 |
| updatedAt                     | BigInt!       | When the minter updated                                                  |

# ProjectMinterConfiguration

Description: get details of a specific mint

| Field              | Type     | Description                                                                        |
| ------------------ | -------- | ---------------------------------------------------------------------------------- |
| id                 | ID!      | Unique identifier made up of minter contract address-projectId                     |
| project            | Project! | The associated project                                                             |
| minter             | Minter!  | The associated minter                                                              |
| priceIsConfigured  | Boolean! | true if project's token price has been configured on minter                        |
| currencySymbol     | String!  | currency symbol as defined on minter - ETH reserved for ether                      |
| currencyAddress    | Bytes!   | currency address as defined on minter - address(0) reserved for ether              |
| purchaseToDisabled | Boolean! | Defines if purchasing token to another is allowed                                  |
| basePrice          | BigInt   | price of token or resting price of Duch auction, in wei                            |
| startPrice         | BigInt   | Dutch auction start price, in wei                                                  |
| halfLifeSeconds    | BigInt   | Half life for exponential decay Dutch auction, in seconds                          |
| startTime          | BigInt   | Dutch auction start time (unix timestamp)                                          |
| endTime            | BigInt   | Linear Dutch auction end time (unix timestamp)                                     |
| extraMinterDetails | String!  | Configuration details used by specific minter project configurations (json string) |

# Payment

Description: get details of payment for an NFT

| Field        | Type         | Description                                                                                       |
| ------------ | ------------ | ------------------------------------------------------------------------------------------------- |
| id           | ID!          | Payment id formatted: '{SaleId}-{paymentNumber}' (paymentNumber will be 0 for non-Seaport trades) |
| paymentType  | PaymentType! | Type of token transferred in this payment                                                         |
| paymentToken | Bytes!       | The address of the token used for the payment                                                     |
| price        | BigInt!      | The price of the sale                                                                             |
| sale         | Sale!        | The associated sale                                                                               |
| recipient    | Bytes!       | The recipient address                                                                             |

# Sale

Description: get sale information

| Field             | Type                                 | Description                                                                                                                                                  |
| ----------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id                | ID!                                  | The sale id formated: tokenId - token.nextSaleId (using first token sold for bundles) for Opensea V1/V2, orderHash from sale event for Looksrare and Seaport |
| txHash            | Bytes!                               | The hash of the transaction                                                                                                                                  |
| exchange          | Exchange!                            | The exchange used for this sale                                                                                                                              |
| saleType          | SaleType!                            | The sale type (SingleBundle)                                                                                                                                 |
| blockNumber       | BigInt!                              | The block number of the sale                                                                                                                                 |
| blockTimestamp    | BigInt!                              | The timestamp of the sale                                                                                                                                    |
| summaryTokensSold | String!                              | A raw formated string of the token(s) sold (i.e TokenID1::TokenID2::TokenID3)                                                                                |
| saleLookupTables  | [SaleLookupTable!](#salelookuptable) | Lookup table to get the list of Tokens sold in this sale                                                                                                     |
| seller            | Bytes!                               | The seller address                                                                                                                                           |
| buyer             | Bytes!                               | The buyer address                                                                                                                                            |
| payments          | [Payment!](#payment)                 | List of Payment tokens involved in this sale                                                                                                                 |
| isPrivate         | Boolean!                             | Private sales are flagged by this boolean                                                                                                                    |

# SaleLookupTable

Description:

| Field       | Type     | Description                           |
| ----------- | -------- | ------------------------------------- |
| id          | ID!      | Set to `Project Id::Token Id::Sale Id |
| blockNumber | BigInt!  | The block number of the sale          |
| timestamp   | BigInt!  | Timestamp of the sale                 |
| project     | Project! | The associated project                |
| token       | Token!   | The token sold                        |
| sale        | Sale!    | The associated sale                   |

# Transfer

Description: transfer info on an NFT

| Field           | Type    | Description                   |
| --------------- | ------- | ----------------------------- |
| id              | ID!     | Unique identifier of transfer |
| transactionHash | Bytes!  | trasaction hash of transfer   |
| token           | Token!  | token address of NFT          |
| createdAt       | BigInt! | when transfer initiated       |
| to              | Bytes!  | address transferred to        |
| from            | Bytes!  | address transferred from      |

# ProjectExternalAssetDependency

Description: get info about projects external asset dependency

| Field          | Type                                | Description                                  |
| -------------- | ----------------------------------- | -------------------------------------------- |
| id             | ID!                                 | Unique identifier made up of projectId-index |
| project        | Project!                            | The associated project                       |
| dependencyType | ProjectExternalAssetDependencyType! | The dependency type                          |
| cid            | String!                             | The dependency cid                           |
| index          | BigInt!                             | The dependency index                         |
