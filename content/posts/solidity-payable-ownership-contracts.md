---
title: "Solidity Payable Ownership Contracts"
date: 2022-01-17T09:21:56-08:00
draft: false
---


Building foreverawards.com, I have built a basic minter and it works well enough to move to the next level, charging for the service to mint an award that the wallerholder sends to their teammate.

## Contracts

When ever talking about charging, transfering, or components of, we are talking about [Contracts](https://docs.soliditylang.org/en/v0.5.10/contracts.html), which is on v0.8 at the moment of writing this post in the soliditylang documentation site.

### Visibility and Getters

`external`, can be used in transactions from other contracts. `public` are part of the contract interface and can be called internally or via `messages`. `internal`, default visibility for state variables and can only be called within the contract without using this. `private` state is held in the contract only and cannot be derived - this prevents other contracts from reading state.

`public` can be used internally or externally via the `this` keyword from within the contract.


## Payable
The contracts balance can increase but what about withdrawing the balance, only the contract creator should be able to do this. Payable is that keyword and ownership is defined below.

* [Payble](https://solidity-by-example.org/payable/) is a keyword in Solidity where a contract can receive either.
* [StackOverflow lead to explinations](https://ethereum.stackexchange.com/questions/20874/payable-function-in-solidity).

## Ownership

[Access Control](https://docs.openzeppelin.com/contracts/3.x/access-control) - When talking about smart contracts `who can do what` is the basic point. There is a an account that can do `administration` tasks, we link to openzepplin which is a great opensource interface to help make common concepts easier to use. Using their [Ownable](https://docs.openzeppelin.com/contracts/4.x/api/access#Ownable) package by default, `the owner of an Ownable contract is the account that deployed it.` quote from the documentation.

It has a [modifier](https://docs.soliditylang.org/en/v0.8.10/contracts.html#function-modifiers) called `onlyOwner` which basically says the owner of the contract can do the administration task.