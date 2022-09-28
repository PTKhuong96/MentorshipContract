# CW721 Metadata Onchain

NFT creators may want to store their NFT metadata on-chain so other contracts are able to interact with it.
With CW721-Base in CosmWasm, we allow you to store any data on chain you wish, using a generic `extension: T`.

In order to support on-chain metadata, and to demonstrate how to use the extension ability, we have created this simple contract.
There is no business logic here, but looking at `lib.rs` will show you how do define custom data that is included when minting and
available in all queries.

In particular, here we define:

```rust
#[derive(Serialize, Deserialize, Clone, PartialEq, JsonSchema, Debug)]
pub struct Metadata {
    pub group_id: Option<String>,
    pub type: Option<String>,
    pub summary: Option<String>,
    pub agenda: Option<String>,
    pub mentor: Option<String>,
    pub duration: Option<u32>,
    pub expiration_date: Option<String>,
    pub method: Option<String>,
    pub location: Option<String>,
    pub created_date: Option<String>,
}

pub type Extension = Option<Metadata>;
```

Please look at the test code for an example usage in Rust.

## Notice

Feel free to use this contract out of the box, or as inspiration for further customization of cw721-base.
We will not be adding new features or business logic here.
