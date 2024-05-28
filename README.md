## Foundry

**Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

-   **Forge**: Ethereum testing framework (like Truffle, Hardhat and DappTools).
-   **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions and getting chain data.
-   **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
-   **Chisel**: Fast, utilitarian, and verbose solidity REPL.

## Documentation

https://book.getfoundry.sh/

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### Format

```shell
$ forge fmt
```

### Gas Snapshots

```shell
$ forge snapshot
```

### Anvil

```shell
$ anvil
```

### Deploy

```shell
$ forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
$ cast <subcommand>
```

### Help

```shell
$ forge --help
$ anvil --help
$ cast --help
```

# Assembly
[Solidity Docs - Inline Assembly](https://docs.soliditylang.org/en/latest/assembly.html)<br>
[Solidity Docs - Yul](https://docs.soliditylang.org/en/latest/yul.html#yul)<br>
> Inline assembly is a way to access the Ethereum Virtual Machine at a low level. This bypasses several important safety features and checks of Solidity. You should only use it for tasks that need it, and only if you are confident with using it.

An inline assembly block is marked by `assembly { ... }`, where the code inside the curly braces is code in the `Yul` language.

Different inline assembly blocks share no namespace, i.e. it is not possible to call a Yul function or access a Yul variable defined in a different inline assembly block.

### Synthax
- Variable `declaration`:
```
assembly {
    let x := 123
}
```
An already existing solidity variable can also be assigned a value in Yul:
```
uint256 z;
assembly {
    z := 456
}
```
- Using `if` and `switch` statements
> There is no `else` statement in Yul!
```
uint256 x;
uint256 z;
assembly {
    if lt(x, 10) {z := 99}//note: lt --> "compare if x is `less than` 10"
}
```