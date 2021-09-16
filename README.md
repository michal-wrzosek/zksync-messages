# zksync-messages

Ethereum zkSync messages dapp (proof of concept)

[zinc contract code](messages/src/main.zn)

This contract should allow you to create an account and post short messages.

Later, once the contract starts getting into some stable phase, some frontend will be added here.

# Updates

**2021-09-16**

Trying to deploy first test version of the contract.

**2021-09-15**

Started working on the contract as a zkSync learning.

# ZINC installation

This is an example installation for macOS and zsh. You're free to do it in your way, but the concept stays the same - download, unzip and add directory to the PATH.

Check the latest release https://github.com/matter-labs/zinc/releases

Then download it and unzip in some place:

```
curl -L -o zinc-0.2.3-macos.zip "https://github.com/matter-labs/zinc/releases/download/0.2.3/zinc-0.2.3-macos.zip" && \
  unzip zinc-0.2.3-macos.zip -d ~/ && \
  rm -f zinc-0.2.3-macos.zip
```

Then add this new directory to your PATH (zsh):

```
echo -n 'export PATH=~/zinc-0.2.3-macos:$PATH' >> ~/.zshrc
```

Now this will be available for you:

- `zargo` package manager
- `znc` Zinc compiler
- `zvm` Zinc virtual machine

**Install VSCode zinc extension:**

- [Zinc Syntax Highlighting](https://marketplace.visualstudio.com/items?itemName=hedgar2017.zinc-syntax-highlighting)

**Useful resources:**

- ZINC documentation: https://zinc.zksync.io/

# Notes

**Creating the "messages" contract:**

_The contract name needs to be unique on the network_

```
zargo new --type contract messages
```

**Checking all the contracts deployed to the network**

```
zargo download --list --network rinkeby
```

**Deploying the contract**

if you don't have it, create a `private_key` file with a private key to your test account:

```
touch ./messages/private_key
code ./messages/private_key
```

Edit `./messages/Zargo.toml` file to adjust contract details.
Edit `./messages/data/input.json` file to adjust contract arguments.

```
cd ./messages
zargo publish --network rinkeby --instance default
```
