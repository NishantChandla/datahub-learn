---
description: Learn how to interact with the web3.eth.iban package
---

# Web3.eth.iban

## Source documentation 

[**The web3.eth.Iban package's source documentation can be found here**](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html). 

## web3.eth.Iban

The `web3.eth.Iban` function converts Ethereum addresses from and to IBAN and BBAN.

### `Iban instance`

This instance of Iban.

```javascript
> Iban { _iban: 'XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS' }
```

### `Iban contructor`

```javascript
new web3.eth.Iban(ibanAddress)
```

Generates a iban object with conversion methods and validity checks.

Also has singleton functions for conversion like:

* [Iban.toAddress\(\)](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html#eth-iban-toaddress)
* [Iban.toIban\(\)](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html#eth-iban-toiban)
* [Iban.fromAddress\(\)](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html#eth-iban-fromaddress)
* [Iban.fromBban\(\)](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html#eth-iban-frombban)
* [Iban.createIndirect\(\)](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html#eth-iban-createindirect)
* [Iban.isValid\(\)](https://web3js.readthedocs.io/en/v1.3.0/web3-eth-iban.html#eth-iban-isvalid)

#### Parameters

1. `String`: the IBAN address to instantiate an Iban instance from.

#### Returns

`Object` - The Iban instance.

#### Example

```javascript
var iban = new web3.eth.Iban("XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS");
> Iban { _iban: 'XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS' }
```

### `toAddress`

Static function.

```javascript
web3.eth.Iban.toAddress(ibanAddress)
```

Singleton: Converts a direct IBAN address into an Ethereum address.

**Note**

This method also exists on the IBAN instance.

#### Parameters

1. `String`: the IBAN address to convert.

#### Returns

`String` - The Ethereum address.

#### Example

```javascript
web3.eth.Iban.toAddress("XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS");
> "0x00c5496aEe77C1bA1f0854206A26DdA82a81D6D8"
```

### `toIban`

Static function.

```javascript
web3.eth.Iban.toIban(address)
```

Singleton: Converts an Ethereum address to a direct IBAN address.

#### Parameters

1. `String`: the Ethereum address to convert.

#### Returns

`String` - The IBAN address.

#### Example

```javascript
web3.eth.Iban.toIban("0x00c5496aEe77C1bA1f0854206A26DdA82a81D6D8");
> "XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS"
```

### `fromAddress`

Static function, returns IBAN instance.

```javascript
web3.eth.Iban.fromAddress(address)
```

Singleton: Converts an Ethereum address to a direct IBAN instance.

#### Parameters

1. `String`: the Ethereum address to convert.

#### Returns

`Object` - The IBAN instance.

#### Example

```javascript
web3.eth.Iban.fromAddress("0x00c5496aEe77C1bA1f0854206A26DdA82a81D6D8");
> Iban {_iban: "XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS"}
```

> static function, return IBAN instance

### `fromBban`

```javascript
web3.eth.Iban.fromBban(bbanAddress)
```

Singleton: Converts an BBAN address to a direct IBAN instance.

#### Parameters

1. `String`: the BBAN address to convert.

#### Returns

`Object` - The IBAN instance.

#### Example

```javascript
web3.eth.Iban.fromBban('ETHXREGGAVOFYORK');
> Iban {_iban: "XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS"}
```

> static function, return IBAN instance

### `createIndirect`

```javascript
web3.eth.Iban.createIndirect(options)
```

Singleton: Creates an indirect IBAN address from an institution and identifier.

#### Parameters

1. `Object`: the options object as follows:
   * `institution` - `String`: the institution to be assigned.
   * `identifier` - `String`: the identifier to be assigned.

#### Returns

`Object` - The IBAN instance.

#### Example

```javascript
web3.eth.Iban.createIndirect({
    institution: "XREG",
    identifier: "GAVOFYORK"
});
> Iban {_iban: "XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS"}
```

Static function, returns boolean.

### `isValid`

```javascript
web3.eth.Iban.isValid(ibanAddress)
```

Singleton: Checks if an IBAN address is valid.

**Note**

This method also exists on the IBAN instance.

#### Parameters

1. `String`: the IBAN address to check.

#### Returns

`Boolean`

#### Example

```javascript
web3.eth.Iban.isValid("XE81ETHXREGGAVOFYORK");
> true

web3.eth.Iban.isValid("XE82ETHXREGGAVOFYORK");
> false // because the checksum is incorrect
```

### `prototype.isValid`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.isValid()
```

Singleton: Checks if an IBAN address is valid.

**Note**

This method also exists on the IBAN instance.

#### Parameters

1. `String`: the IBAN address to check.

#### Returns

`Boolean`

#### Example

```javascript
var iban = new web3.eth.Iban("XE81ETHXREGGAVOFYORK");
iban.isValid();
> true
```

### `prototype.isDirect`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.isDirect()
```

Checks if the IBAN instance is direct.

#### Parameters

none

#### Returns

`Boolean`

#### Example

```javascript
var iban = new web3.eth.Iban("XE81ETHXREGGAVOFYORK");
iban.isDirect();
> false
```

### `prototype.isIndirect`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.isIndirect()
```

Checks if the IBAN instance is indirect.

#### Parameters

none

#### Returns

`Boolean`

#### Example

```javascript
var iban = new web3.eth.Iban("XE81ETHXREGGAVOFYORK");
iban.isIndirect();
> true
```

### `prototype.checksum`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.checksum()
```

Returns the checksum of the IBAN instance.

#### Parameters

none

#### Returns

`String`: The checksum of the IBAN

#### Example

```javascript
var iban = new web3.eth.Iban("XE81ETHXREGGAVOFYORK");
iban.checksum();
> "81"
```

### `prototype.institution`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.institution()
```

Returns the institution of the IBAN instance.

#### Parameters

none

#### Returns

`String`: The institution of the IBAN

#### Example

```javascript
var iban = new web3.eth.Iban("XE81ETHXREGGAVOFYORK");
iban.institution();
> 'XREG'
```

### `prototype.client`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.client()
```

Returns the client of the IBAN instance.

#### Parameters

none

#### Returns

`String`: The client of the IBAN

#### Example

```javascript
var iban = new web3.eth.Iban("XE81ETHXREGGAVOFYORK");
iban.client();
> 'GAVOFYORK'
```

### `prototype.toAddress`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.toString()
```

Returns the Ethereum address of the IBAN instance.

#### Parameters

none

#### Returns

`String`: The Ethereum address of the IBAN

#### Example

```javascript
var iban = new web3.eth.Iban('XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS');
iban.toAddress();
> '0x00c5496aEe77C1bA1f0854206A26DdA82a81D6D8'
```

### `prototype.toString`

Method of Iban instance.

```javascript
web3.eth.Iban.prototype.toString()
```

Returns the IBAN address of the IBAN instance.

#### Parameters

none

#### Returns

`String`: The IBAN address.

#### Example

```javascript
var iban = new web3.eth.Iban('XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS');
iban.toString();
> 'XE7338O073KYGTWWZN0F2WZ0R8PX5ZPPZS'
```
