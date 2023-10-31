# 📔 Concepts

#### Dispatcher&#x20;

A dispatcher serves as a traffic controller, ensuring that your transactions are directed to the right destinations within the network. What's great about it is that it eliminates the need for you to manually sign each transaction when interacting with applications and smart contracts. This simplifies the process, making it more user-friendly and convenient, as the dispatcher acts like an automated messenger, carrying out your requests without requiring your personal approval for each action, ultimately enhancing the overall user experience.

{% hint style="warning" %}
Dispatcher works only when you have access to Gasless Transactions
{% endhint %}

#### Gasless Transaction

Gasless Transactions allow you to interact with Lens Protocol without the need to pay gas fees with every interaction. Keep in mind that gasless transactions happen using the dispatcher and than not everyone has acess to it.

{% hint style="warning" %}
Lens believes in supporting content creators and followers who create an engaging environment for everyone. Currently, they use machine learning algorithms to identify high-signal accounts and curated profiles based on factors such as follower graphs, content and other factors. Unfortunately, low-signal, pesty profiles diminish everyone's experience and waste gas. As a way of curtailing flagged, low-signal profiles, we have decided to stop paying gas fees for profiles that do not meet a certain signal threshold and create a nuisance&#x20;
{% endhint %}

#### Profile

The Lens Protocol uses "Profile NFTs" as digital badges to represent your online identity. These badges are linked to digital addresses, and you can have multiple badges for different online profiles. They also help you track your online connections and interactions such as Posts, comments & mirrors. To interact on LensProtocol, you need one of these profiles, each with a unique number.&#x20;

#### Handle

Handle is a new concept which was introduced in Lens v2. Think about Handle as a name on a social network: like @alice, @bob or @vitalik. Handles can exist and can be minted separately from profiles, and then can be linked and unlinked from one profile to another. Handles exist in their own namespaces, and currently the only namespace is lens, so all currently available handles are technically under lens/@alice.

#### Publication

Publications in the Lens Protocol are like different kinds of posts, comments, and mirrors created by users. They are not NFTs, but they're stored in a user's profile. These publications can contain text, images, videos, or other stuff, and you can think of them as content files stored on the internet.

Publications also have two modules: one that controls if and what people can turn them into NFTs, and another that controls who can comment and share them.

{% hint style="info" %}
Publications can be stored in multiple ways therefore "decentralizing it" at difrent level most common options are : IPFS, Arvawe, AWS (Amazon's Hosting)
{% endhint %}

#### Mirror

Mirrors are the curation tool of the Lens Protocol. They are the protocol's equivalent to reposting or re-amplifying content. Mirrors are treated the same as publications with a few additional checks and a few more minor features.

Since mirrors reference other publications, they are subject to the conditions of the original publication's Reference Module. If a publication has a reference module that limits mirrors only to accounts that follow the original poster, and the mirroring account does not hold a Follow NFT, the transaction to mirror will fail.

Since mirrors only repost existing content, they do not have a ContentURI field and therefore cannot be acted on and they don't have an Act module of their own. Mirrors can have their own reference module, which can define what accounts will be able to mirror or comment on the mirror.

#### Data Availability
