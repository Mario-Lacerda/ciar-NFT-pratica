// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/utils/Counters.sol";

contract MeuNFT is ERC721URIStorage {
    using Counters for Counters.Counter;
    Counters.Counter private _tokenIds;

    constructor() ERC721("MeuNFT", "MNFT") {}
    
    function criarNFT(address destinatario, string memory tokenURI) public returns (uint256) {
        _tokenIds.increment();
    
        uint256 novoTokenId = _tokenIds.current();
        _mint(destinatario, novoTokenId);
        _setTokenURI(novoTokenId, tokenURI);
    
        return novoTokenId;
    }
}
