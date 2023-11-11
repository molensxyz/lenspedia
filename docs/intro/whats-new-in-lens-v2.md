# What's new in Lens V2?

Lens V2 is the first big upgrade of the Lens Protocol, it aims to improve the protocol design based on all the learnings after its first year, as well as introduce some new interesting features:

* All the social operations are now Profile-based, instead of address-based, meaning that they require to be performed by a Profile
  * You can no longer follow with an address. All follows are required to be done by a Profile
  * Legacy Collect action, and new Publication Actions are now executed by Profiles (common proxy profiles might be used to support address-based collects if wanted)
* Follow NFTs are optimized for the best UX by not being ERC-721 by default. They now have two states:
  * Unwrapped (default, non-ERC-721 state): Tied to the follower Profile, meaning they move with the follower Profile when it is transferred to a different address
  * Wrapped (opt-in, ERC-721 state): Follow NFTs natively support being wrapped into ERC-721 tokens, to get the best out of composability with other protocols
  * Ownership/Custody of the Follow NFT is no longer related to the following state, the follower profile is set as a field inside the Follow NFT. This enables a lot of interesting use cases and improvements.
* Addition of the Advanced Referral System
* Addition of Publication Action Modules (aka Smart Posts)
* Addition of Delegated Executors (more details below)
* Lens Handles are now ERC721s and managed by a separate contract
* TokenGuardian pattern introduced on both Profiles and Handles to supply additional protection of social assets
* All code was reworked and rewritten from scratch
* Many more fixes and improvements

Many of the things mentioned above introduce breaking changes in the protocol and its interfaces.
