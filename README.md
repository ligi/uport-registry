# uPort Registry

This is the current registry that out mobile app uses. If you need to integrate with the mobile app or our servers. We will eventually move to [this](https://github.com/ConsenSys/uport-registry/) newer, more feature-rich registry.

## Deployed Contracts

The registry has been deployed at the following locations:

- [Ropsten Testnet](https://testnet.etherscan.io/address/0xb9c1598e24650437a3055f7f66ac1820c419a679): `0xb9C1598e24650437a3055F7f66AC1820c419a679`
- [Mainnet](https://etherscan.io/address/0x022f41a91cb30d6a20ffcfde3f84be6c1fa70d60): `0x022f41a91cb30d6a20ffcfde3f84be6c1fa70d60`

## About

The uPort registry is a single contract where uport identities can 'self-attest' to data about themselves. This is done by uploading a json object to IPFS, and then signing the corresponding IPFS address into the registry contract.

Right now we are focusing on

* Full Name
* Profile Picture

We intend to support the full [Schema.org Person schema](http://schema.org/Person). The Full Name and Profile Picture is stored in IPFS as a JSON structure that corresponds to the schema.org schema:

```json
{
   "@context": "http://schema.org/",
   "@type": "Person",
   "name": "Christian Lundkvist",
   "image": [{"@type": "ImageObject",
             "name": "avatar",
             "contentUrl" : "/ipfs/QmUSBKeGYPmeHmLDAEHknAm5mFEvPhy2ekJc6sJwtrQ6nk"}]
}
```

and an IPFS hash of this structure is stored in the contract as a `bytes` structure.

