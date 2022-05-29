# Celestial
The contract for the Celestial drop. Uploaded for auditing purposes.


Site: https://0xcelestial.com/


# Important Functions

- distortionClaimByToken(uint256[] memory  _tokenIds)
  - Allows Distortion holders to claim N CLST token per N DST token they hold.
  - Increments `distortionTokenIdClaimed[tokenId]` mapping to disallow double claims.
  - Sets token level to 3 and creates the initial token transfer timestamp in a mapping.


- distortionMergeClaim(uint256[] memory  _tokenIds)
  - Allows Distortion holders to claim 1 CLST token per N DST token they hold.
  - Increments `distortionTokenIdClaimed[_tokenIds[i]]` to disallow double claims.
  - Only mints one token with a boosted level `tokenLevels[_tokenIds[i]]`


- publicMint()
  - Doesn't require `nonReentrant` modifier (?) 
    - onePerWallet[msg.sender] is incremented before minting.
  - Mints a level 1 token (`tokenLevels[tokenId] == 0`)


- upgradeToken(uint256 _tokenId)
  - Cannot work if token is already level 100.
  - Must be held for 7 days before function can be called.
  - `tokenTransferredTimestamp[_tokenId]` is set to `block.timestamp` to reset the timer.
  
  
- bulkUpgradeTokens(uint256[] memory _tokenIds)
  - Similar to upgradeToken but with a for loop.


- safeTransferFrom `override` (Will this override work properly and not be exploitable?)


- transferFrom `override` (Will this override work properly and not be exploitable?)

