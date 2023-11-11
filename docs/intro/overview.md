# Overview

The purpose of the Lens Protocol is to empower creators to own the links between themselves and their community, forming a fully composable, decentralized social graph. This is achieved by allowing users to create profiles and interact with each other via these profiles. "Profile" (as used here) refers specifically to Lens profiles; "user" refers to standard crypto-wallets.

The protocol is built from the ground up with modularity in mind. Lens Protocol is currently overseen by a multisig, which will be expanded to a broader DAO, which can develop and vote on new modules and expanded functionality.

### Architecture

Let's first dig into profile creation and publishing. Users must create a profile on the hub, for which they will receive a sequentially ID'd profile NFT. This NFT controls the profile, and thus, its owner becomes the de facto controller of the given profile.

Profile owners can:

1. Publish to the profile. Publication types are:
   1. Post: A standard piece of content.
   2. Comment: A standard piece of content with a pointer to another publication.
      1. Since comments include a pointer, this executes the pointed publication's "reference module" logic, if any.
   3. Quote: Very similar to Comment, also with a pointer to another publication, but usually shown as a separate publication on a timeline
   4. Mirror: The equivalent of a "share" in a traditional sense, having no content but a pointer to another publication.
      1. Since mirrors only include a pointer, this executes the pointed publication's "reference module" logic, if any.
2. Set the profile's "follow module":
   1. This logic contract determines the logic that must be executed when a wallet attempts to follow the given profile; for example, some followers may incur a fee to the profile owner via the fee follow module contract.
3. Set the profile's metadata URI
4. Set the profile's "Delegated Executors" (aka Profile Managers):
   1. This is an address that can act on behalf of a profile's owner; it can:
      1. Publish to the given profile.
      2. Follow
      3. Act
      4. Set the given profile's metadata URI.
5. Follow other profiles:
   1. This executes the profile's "follow module" logic, if any.
   2. This creates a "follow NFT" unique to that profile and sequentially ID'd and is tied to the following profile.
      1. Follow NFTs can be wrapped into a regular ERC721
      2. And unwrapped again to be tied to the profile
6. Act on publications:
   1. This executes any logic in the publication's "Action module."

#### Tokenization

The Lens protocol has three layers of tokenization via ERC721 NFTs. All three are ERC721-compliant and fully composable.

The `LensHub` upgradeable contract is the core entry point for the majority of interactions in the Lens Protocol. Nearly all interactions begin and doubles as the ERC721 NFT contract for profile NFTs, which are minted upon profile creation.

Upon a profile's first follow, a `FollowNFT` contract is deployed (via minimal proxy cloning), unique to the profile; this is the ERC721 NFT contract that represents follower positions.

Users can also mint Handles NFTs and link them to their profiles (and unlink at any time to be linked to another profile).

#### Modularity

Modularity is at the core of the Lens protocol. Everything is built with community expansion and the continued development of new, innovative features in mind.

Modules are standalone, governance-whitelisted contracts that adhere to a specific interface. They hold state and are unlimited in potential scope beyond adhering to the interface.

There are three types of modules:

1. Follow modules:\
   a. These modules are tied to a profile and contain logic to be executed upon a user attempting to follow the given profile.
2. Action modules:\
   a. These modules are tied to specific publications (except mirrors, which cannot be acted on) and contain logic to be executed upon a user attempting to act on the given publication.
3. Reference modules:\
   a. These modules are tied to specific publications and contain logic to be executed upon a user attempting to comment or mirror the given publication.\
   b. Note that the original content and its reference module are used in the case where a mirror attempts to point to a mirror.

### Closing Notes

The Lens Protocol is a composable social graph protocol built to be community-owned and ever-evolving. It empowers its users by allowing them to decide _how_ they want their social graph to be built and how they want it to be monetized, if at all.

Furthermore, the protocol is engineered with the concept of modularity at its core, allowing for an infinitely expanding amount of use cases. This, from the user's perspective, translates to a new paradigm of ownership and customization that isn't possible (or financially feasible) in Web2.
