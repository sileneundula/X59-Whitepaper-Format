# X59-Whitepaper-Format
The X59 Data Serialization Technique That Remains Modular, Simplistic, and Easy To Read.

## Preface

Developed and Introduced By Joseph Paul Tortorelli.

## Abstract

Data Serialization is the methodology in which we serialize (or store) our data in different format. There are many data serialization techniques, like JSON, YAML, TOML, PICKLE, and others. In this paper, I would like to introduce a new data serialization / modular data storage technique known as the X59 format, or `X59-fmt`. These method is easy to read, requires little knowledge to be used, and can be used in situations where more context is needed to be added to data. As it is modular, it has the ability to abstract different concepts and rely on other libraries for usage. This data serialization/storage method can be used in many scenarioes, quite like MultiAddr/MultiFormats by Protocol Labs. In this technique, we introduce concepts learned from multiformats into real-life situations and how we can standardize interoperability between different hosts.

`X59-fmt` was developed for the purpose of creating a modular format that can be used to describe data, quite like multiformats. It was developed for use in cryptography but has now been developed for use in other purposes. Due to its extendable nature, it can remain a core component of data serialization.

## Introduction

The concept of `X59-fmt` came from my development of hybrid keypairs known as ShulginSigning (ED25519/ED448 and SPHINCS+ with hedged signatures). The format was intended for public key certificates but after seeing its usefulness in other scenarioes, it began to be applied to other concepts.

## 2. The Core Concepts

### 2.1 X59Labels | (`[(!..)]` or `[]`)

An `X59Label` is defined as the following:

1. has atleast one piece of identifying information, forming a path using the path delimiter `/`
2. has or does not have an attribute, an attribute defined as contextual information using the `X59source`, likely, the `X59STD`. Attributes are defined in braces `[]` with parathesis and an exclamation point `[(!..)example/path/value]`

#### Code Definitions

##### X59Label: Rust

```rust
pub struct X59Label {
  pub pieces: Vec<String>,
  pub attribute: Option<String>,
}
```
##### X59Label: Python
```python
class X59Label:
  pieces: [str]
  attribute: str
```

### 2.2 X59Source | (`@`)

An `X59Source` is defined as the following:

1. contains a `source_identifier` (`SID`)
2. can contain additional information in regards to how it should be parsed

### 2.3 X59Type | (`#`)

An `X59Type` is defined as the following:

1. Defines the data type(s) being serialized using a modular approach.
2. Can use Standard Library, or modular approaches for Type System.
3. Meant to be interoperable (purpose)

### 2.4 X59ConstraintsAndScripting | (`$`)

An `X59Ext` extends on the idea of data formats and makes it so that certain actions can be performed, or even such that certain parsing is performed right and verified.

An `X59Ext` is defined as the following:

1. Using some script/process that is available in the standard library or that is available in registries.
2. ...

## 3. The Value Format

### 3.1 Values

Values are easily readable and follow certain formats making them easy to read, easy to use, and also powerful with extensions.

For example, the value for ShulginSigning of the public keys uses the format below:

`<ED25519_PK>:<SPHINCS+_PK>`

Which can further be interpreted as:

`[librustysigs/shulginsigning]<ED25519_PK>:<SPHINCS+_PK>`

### 3.2 Value Seperation [`: :: ,`]

Values are seperated by either a colon (`:`), two colons (`::`), or a comma (`,`).

### 3.3 Structured Data [`{}`]

Structured Data uses a different format using curly brackets `{}`.

A value can be assigned using the colon inside curly brackets. Prepended to the bracket is the X59Label and an Identifier Value.

```
[librustysigs/shulginsigning][!(structured)] example {

public_key: <pk>;
secret_key: <sk>;

}
```

### 4.0 Splitting Data (`;`)

A semicolon is used to end a data entry.


