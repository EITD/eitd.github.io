---
layout: post
section-type: post
has-comments: true
title: "Failure Detectors"
category: distributed advanced
---

# Properties

- Strong Completeness: Every crashed process is eventually detected by all correct processes.
- Weak Completeness: Every crashed process is eventually detected by some correct process.
- Strong Accuracy: No correct process is ever suspected.
- Weak Accuracy: There exists a correct process P which is never suspected by any process.
- Eventual Strong Accuracy: After some finite time the FD provides strong accuracy.
- Eventual Weak Accuracy: After some finite time the detector provides weak accuracy.

# Classes

Four detectors with **strong completeness**

1. Perfect Detector(P) Strong Accuracy
2. Strong Detector(S) Weak Accuracy
3. Eventually Perfect Detector(◊P) Eventual Strong Accuracy
4. Eventually Weak Detector(◊S) Eventual Weak Accuracy

Four detectors with **weak completeness**

1. Detector Q Strong Accuracy
2. Weak Detector(W) Weak Accuracy
3. Eventual Detector Q(◊Q) Eventual Strong Accuracy
4. Eventual Weak Detector(◊W) Eventual Weak Accuracy

# Leader Election

## VS. Failure Detector

- Leader election (LE) which “matches” P
- Eventual leader election (Ω) which “matches” ♢P

## Properties of LE

- LE1 (eventual completeness). Eventually every correct process trusts some correct process
- LE2 (agreement). No two correct processes trust different correct processes
- LE3 (local accuracy). If a process is elected leader by pi, all previously elected leaders by pi have crashed

## Properties of ELD

- ELD1 (eventual completeness). Eventually every correct node trusts some correct node
- ELD2 (eventual agreement). Eventually no two correct nodes trust different correct node

# Reductions

We say X≼Y if

- X can be solved given a solution of Y
- Read X is reducible to Y
- Informally, problem X is easier or as hard as Y

We write X≃Y if

- X≼Y and Y≼X
- Problem X is equivalent to Y

We write X≺Y if

- X≼Y and not X≃Y
- or equivalently, X≼Y and not Y≼X
- Problem X is strictly weaker than Y, or
- Problem Y is strictly stronger than X

## Completeness “Irrelevant”

- Strong completeness reducible to weak
    - P≼Q, S≼W, ◊P≼◊Q, ◊S≼◊W,
    - P≃Q, S≃W, ◊P≃◊Q, ◊S≃◊W

## Ω and ◊S

- ◊S≼Ω
- Ω≼◊S
- Ω≃◊S