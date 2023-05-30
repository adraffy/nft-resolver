# nft-resolver
On-chain ENS [Wildcard](https://docs.ens.domains/ens-improvement-proposals/ensip-10-wildcard-resolution) NFT Owner-tracking Resolver Contract

## [NFTResolver.sol](./NFTResolver.sol)

Mainnet Deployment: [0x56942dd93A6778F4331994A1e5b2f59613DE1387](https://etherscan.io/address/0x56942dd93a6778f4331994a1e5b2f59613de1387) ⭐️
* Deployment Gas: [1.7m](https://etherscan.io/tx/0x09494aabf187274876eeef22cfb65ef2eb6523c4efab167f3d12cfb2e5861f26) — *not optimized, has nonessential helpers*
* Public Registration Price: [0.01e or 1e16 wei](https://etherscan.io/address/0x56942dd93a6778f4331994a1e5b2f59613de1387#readContract#F9)
* [Additional Information](https://discuss.ens.domains/t/nftresolver-on-chain-wildcard-nft-owner-tracking-resolver/17073)

### Known Bugs in Mainnet Deployment
 
1. `2023-05-29` — when resolving a name that matches an NFT registration, assume `chonks` &rarr; `0xE68d1aEeE2C17E43A955103DaB5E341eE439f55c` and resolve `chonks.eth`, the contract [incorrectly returns the address of resolver itself](https://twitter.com/adraffy/status/1663313066866651136) rather than the address of the NFT.

### Improvement Ideas

* Separate Registry (`label` &rarr; `address`) from Resolver so upgrades are possible.
* Determine best method for registry updates:
	* Price to Register — *current solution*
	* Transaction from [EIP-173](https://eips.ethereum.org/EIPS/eip-173) `owner()`
	* Signed `label` from `owner()`
	* Matching `label.eth` owner
	* Price to Overwrite