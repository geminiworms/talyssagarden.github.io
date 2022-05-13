---
title: alchemy course
---
These are my notes from a course series by [Alchemy](https://www.alchemy.com/) <br>
[My GitHub Repo](https://github.com/geminiworms/alchemyR2W3)

### Week 1: How to develop an NFT smart contract (ERC721) w/ alchemy
[Video](https://www.youtube.com/watch?v=veBu03A6ptw&list=TLPQMDEwNTIwMjIuPY0StW4EGA&index=2) /
[Documentation](https://docs.alchemy.com/alchemy/guides/how-to-develop-an-nft-smart-contract-erc721-with-alchemy) <br>

**What is a smart contract?** A piece of software that runs on a decentralized network of nodes (servers) <br>
What is needed? <br>
1. solidity (language)
2. node (alchemy)
3. dev environment
4. cryptocurrency <br>
**Goals: How to write a smart contract, get test eth, how to use alchemy, deploy to blockchain, how to interacts with NFTs on opensea**
#### writing a smart contract
using [OpenZepplin](https://docs.openzeppelin.com/contracts/4.x/wizard) and Remix IDE <br>
- using the wizard allows you to write a smart contract without self-coding
- "NAME" is the project name, "SYMBOL" is coin symbol <br>
Features: <br>
- Mintable: yes, of course
- Auto increment IDs: individual id's for each object
- Enumerable: checks value of accounts (whether or not a wallet/account has the token i think?)
- URI storage: metadata storage (i.e. exact token ID) 
- Ownable: specifies ownership of project, not individual NFT
- Countable: NFTs are countable <br>
*you can always check the documentation on the openzepplin for troubleshooting*
**now OPEN IN REMIX** <br>
#### modifying a smart contract with remix
- what is remix? "IDE" integrated developer environment, made to deploy solidity smart contracts <br>
- first line ` // SPDX-License-Identifier: MIT ` specifies contract is open source but not to be used for commercial purpose <br>
- private contract `Counters.Counter private _tokenIdCounter` indicates variables that are not going to be accessible externally
- the mint function: <br>
```
    function safeMint(address to, string memory uri) public onlyOwner {
        uint256 tokenId = _tokenIdCounter.current();
        _tokenIdCounter.increment();
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
    }
```
in these parts, variables specify that the mint happens directly to address, it is a public function (accessible to external users interacting with my smart contract), `onlyOwner` right now means that only the contract owner is allowed to mint... so we deleted that, as well as other lines indicating `ownable` (see below)
- deleted lines: `import "@openzeppelin/contracts@4.6.0/access/Ownable.sol";`
- regarding the overrides, the notable one is the `function tokenURI(uint256 tokenId)` as it allows platforms like Opensea to get the URI of your token
- `internal` variables/functions readable by smart contracts inheriting from ours
- `view` variables/functions are only reading from the blockchain (not writing), marking as `view` is a no gas interaction with the blockchain <br>
**modifications:**
- setting max supply (of 10,000)
```
    Counters.Counter private _tokenIdCounter;
    uint256 MAX_SUPPLY = 10000;
```
- sold out message when max supply is reached
```
function safeMint(address to, string memory uri) public {
        uint256 tokenId = _tokenIdCounter.current();
        require(tokenId <= MAX_SUPPLY, "I'm sorry all NFTs have been minted");
        _tokenIdCounter.increment();
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
    }
```
<br>
The final contract:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.4;

import "@openzeppelin/contracts@4.6.0/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts@4.6.0/token/ERC721/extensions/ERC721Enumerable.sol";
import "@openzeppelin/contracts@4.6.0/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/utils/Counters.sol";


contract Talytest is ERC721, ERC721Enumerable, ERC721URIStorage {
    using Counters for Counters.Counter;

    Counters.Counter private _tokenIdCounter;
    uint256 MAX_SUPPLY = 10000;

    constructor() ERC721("talytest", "TEST") {}

    function safeMint(address to, string memory uri) public {
        uint256 tokenId = _tokenIdCounter.current();
        require(tokenId <= MAX_SUPPLY, "I'm sorry all NFTs have been minted");
        _tokenIdCounter.increment();
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
    }

    // The following functions are overrides required by Solidity.

    function _beforeTokenTransfer(address from, address to, uint256 tokenId)
        internal
        override(ERC721, ERC721Enumerable)
    {
        super._beforeTokenTransfer(from, to, tokenId);
    }

    function _burn(uint256 tokenId) internal override(ERC721, ERC721URIStorage) {
        super._burn(tokenId);
    }

    function tokenURI(uint256 tokenId)
        public
        view
        override(ERC721, ERC721URIStorage)
        returns (string memory)
    {
        return super.tokenURI(tokenId);
    }

    function supportsInterface(bytes4 interfaceId)
        public
        view
        override(ERC721, ERC721Enumerable)
        returns (bool)
    {
        return super.supportsInterface(interfaceId);
    }
}
```

#### let's deploy!
- create new app on [Alchemy](https://www.alchemy.com/) and copy the HTTP key
- in metamask, add new network "Alechmy Rinkeby" and paste the HTTP key into RPC url field
- getting rinkeby from [faucet](https://rinkebyfaucet.com/) and link alchemy for additional 0.5eth deposit <br>
**back in remix**
- enter solidity compiler tab (left hand bar) and make sure compiler corresponds to contract line 2 `pragma solidity ...`
- turn on auto compile
- enter deploy & run transactions tab and connect to environment INJECTED WEB3, which will ask you for a wallet connection and ultimately connect you back to alchemy
- select CONTRACT by NAME (in my case, talytest), and then it'll open your wallet to pay for gas to deploy it
- in "DEPLOYED CONTRACTS" tab dropdown, you can see the orange and blue functions... orange means it's writing to blockchain, blue is viewing blockchain <br>
#### minting 
create metadata [opensea metadata standard](https://docs.opensea.io/docs/metadata-standards) <br>
- copy and paste the opensea metadata standard into a text editor (json file) i.e. Notepad++
- upload an image with [filebase](filebase.com) and create a new bucket with IPFS storage network (unchanging file)
- copy and paste the IPFS Gateway URL into the json file
```json
"image": "https://ipfs.filebase.io/ipfs/bafkreiftim7yp4sfwaknbyio4uvjzwf6yka2boekuk56ybf3an6tfazhqa"
```
- input relevant traits and then save and upload the .json file into the same filebase bucket
- copy the metadata IPFS CID and paste into remix dropdown SAFEMINT variable to wallet address, make sure to add ipfs:// before the IPFS CID 
- remix shows that I successfully minted, but it wont show up on opensea testnet... <br>

OpenSea testnet still doesnt show it, but I got a tip to use rinkeby rarible and that was [successful](https://rinkeby.rarible.com/token/0xf97a3e94ec24f2358e992cca35d3af562ad9d4ae:0?tab=details)
