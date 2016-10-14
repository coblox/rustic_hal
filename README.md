# Rustic Hal

A simple library for serializing (and deserializing coming soon) resources following the [HAL Spec](https://tools.ietf.org/html/draft-kelly-json-hal-08)

## Usage

Add the dependency to your Cargo.toml:

```toml

[dependencies]
rustic_hal="0.0.1"
serde="0.8"
serde_json="0.8"
serde_derive="0.8"

```
and to use:

```rust

extern crate rustic_hal;
extern crate serde;
extern crate serde_json;

use rustic_hal::*;
use serde::Serialize;
use serde_json::to_json;

#[derive(Serialize)]
pub struct MyResource {
    pub test: String;
}

let mr = MyResource { test: "Hello, World!".to_string() };
let mut hal_res = HalResource::new(mr);
hal_res.add_link("self", "/api/myresource/0");

println!("json representation: {}", to_json(hal_res));

```

## Credits

This library is heavily inspired by (read copied from) the [hal-rs](https://github.com/hjr3/hal-rs) library by Herman J. Radtke III.

## Warnings

I have only very recently started learning Rust, so the idiomatic quality of  this code is probably very low.

   



