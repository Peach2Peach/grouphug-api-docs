---
title: GroupHug API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

includes:
  - system
  - queue
  - batch


search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the GroupHug API
---

# Introduction

Batching server that allows combining PSBT into a single batched transaction.

The PSBTs have to be payouts in full (ie no change). Otherwise, the change output can be stolen.
In other words, only PSBTs with 1 input and 1 output are accepted.
The PSBT inputs have to be signed with `SINGLE|ANYONECANPAY` sig hash.

The batching server collects all PSBTs and when a threshold is reached, all PSBTs are combined, an extra fee output added and then each input is signed by the server with the default `ALL` sig hash.

The batching server will also add one additional output for optional donations to the service. The extra output value is calculated by summing up all inputs and subtracting the mining fees.
