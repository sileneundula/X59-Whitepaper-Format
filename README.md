# X59-Whitepaper-Format
The X59 Data Serialization Technique That Remains Modular, Simplistic, and Easy To Read.

## Preface

Developed and Introduced By Joseph Paul Tortorelli.

## Abstract

Data Serialization is the methodology in which we serialize (or store) our data in different format. There are many data serialization techniques, like JSON, YAML, TOML, PICKLE, and others. In this paper, I would like to introduce a new data serialization / modular data storage technique known as the X59 format, or `X59-fmt`. These method is easy to read, requires little knowledge to be used, and can be used in situations where more context is needed to be added to data. As it is modular, it has the ability to abstract different concepts and rely on other libraries for usage. This data serialization/storage method can be used in many scenarioes, quite like MultiAddr/MultiFormats by Protocol Labs. In this technique, we introduce concepts learned from multiformats into real-life situations and how we can standardize interoperability between different hosts.

X59-fmt was developed for the purpose of creating a modular format that can be used to describe data, quite like multiformats. It was developed for use in cryptography but has now been developed for use in other purposes. Due to its extendable nature, it can remain a core component of data serialization.

## Introduction

The concept of `X59-fmt` came from my development of hybrid keypairs known as ShulginSigning (ED25519/ED448 and SPHINCS+ with hedged signatures). The format was intended for public key certificates but after seeing its usefulness in other scenarioes, it began to be applied to other concepts.

## 2. The Core Concepts

### 2.1 X59Labels

An `X59Label` is defined as the following:

```python
class X59Label:
  pieces: [str]
  attribute: str

```

```rust

pub struct X59Label {
  pub pieces: Vec<String>,
  pub attribute: Option<String>,
}


```

