---
layout: default
title: How to find other participants?
permalink: /docs/orgid/discover/
parent: Marketplace
nav_order: 2
---

# How to find other participant's ORGiD?

There are two ways to find other participants:

* Using a User Interface
* Interacting with the ORGiD smartcontract

## Using the Marketplace User Interface

Winding Tree hosts a user-friendly interface where it is possible to explore the various organizations participating in the Winding Tree marketplace.

* In live environment: [https://marketplace.windingtree.com/search](https://marketplace.windingtree.com/search)
* In test environment: [https://staging.arbor.fm/search](https://staging.arbor.fm/search)

You will need to have an Ethereum wallet such as [Metamask](https://metamask.io).

## Using the ORGiD Smartcontract

Using the smartcontract, it is possible to gather all details of the organizations participating to the marketplace.

_Before you start, make sure you are able to [connect to an Ethereum node and have retrieve the contract ABI](/docs/orgid/connect/)._

### Use Cases

Interacting directly with the ORGiD smartcontract allows to create a snapshot of all participants at a given time. Since it is ressource extensive, it is typically used to build a cache in the following cases:

* _I am an innovative Travel Agency and I want to keep track of all available hotels._
* _I am a Corporate and I want to keep track of all available airlines._
* _I am an airline and I want to associate my negotiated rates with the proper Corporate's ORGiD identifier._

### Building a cache

Using the organization details stored in the smartcontract, it is possible to retrieve the associated JSON document that contains all the details of the organization.

The process would be as follow:

1. Retrieve all organizations from the ORGiD smartcontract using the `getOrganizations` method
2. For each organization, use the `getOrganization` method to retrieve the JSON document URIs and the associated fingerprint hash
3. For each organization, using the JSON document URI, retrieve the document, verify its compliance with the [JSON Schema](https://github.com/windingtree/org.json-schema) and verify the file signature against the fingerprint hash
4. Do some extra validation on the trust proofs provided
5. Store the data in a Database or other cache mechanism

__Note__: The steps 1-4 are implemented in the open-source [ORGiD Resolver](https://github.com/windingtree/org.id-resolver/)
