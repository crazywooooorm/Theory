# Blockchain

## Cryptology

### Collision Resistance
* Cryptographic hash function (H)
* Collision: x != y but H(x) = H(y)
* Collision Resistance: for any m, can't find m' to make H(m') = H(m)
* MD5 used to be a good hash function (collision resistance), while people has found ways to break its collision resistance

### Hiding
* x -> H(x), but you can't find x from H(x)
* Sealed envelope
* Practical case: if the input set of H is too small (people can find x by trying all the possible input values), we can add some nonce (H(x||nonce)) to keep x hided.

### Puzzle friendly
* You can't predict H(x) from x without really calculating H(x). You can't know which x are more likely to generate the H(x) with specific pattern (target space). This feature is used for 'proof of work' in blockchain.
* Difficult to solve but easy to verify
* SHA-256 is considered as a secure hash algorithm with all three features listed above

### Asymmetric encryption algorithm
* Keys for encryption (public key) and decryption (private key) are different.
* Public key is like account number and private key is like password.
* Use private key to sign and use public key to verify the sign.

## Hash pointers
* Hash pointers stores both the origin address and H value.
* For a blockchain, each block has the hash pointer which points to the most recent blocks. The Hash value is also created from the most recent block. This structure creates a tamper-evident log, any changes for any previous block will change all the hash values after.
* Merkle tree: the lowest leaves are data blocks, all the nodes above are hash pointers calculated by lower nodes. Any changes in any place in the tree will change the root hash.

## Consensus in BitCoin
* Each block in blockchain has to verity two things: the source of the transaction (member) and the source of the coin (coinbase, to avoid the double spending attack)
* Block header includes: version (of agreement), hash of previous block header (hash pointer), merkle root hash, target (mine target) and nonce. Only hash values of hash headers are calculated and transferred.
* Block body includes: data
* Whether transactions are legal is decided by the vote of members.
* Once the vote is based on accounts, Sybil attack (create a large number of fake accounts) would be an potential way to control the whole voting system. In BitCoin system, vote is based on computation power (theoretically). Only the member with the largest computation power (who solve the puzzle quickest) is allowed to wrap up the block and publish it.
* Forking attack happens when the block is not published on the longest valid chain, which causes conflict with the existing blocks.
* In BitCoin system, it is possible that two blocks are published at the same time and all connect to the last block of the longest valid chain. In this case, the winner block would be the one having an earlier next block connected to it. The loser would become an orphan block and gets dropped.
* Bitcoin block reward: Coinbase transaction, the only way to generate new bitcoin.

## Real Practice
* All the unspent BitCoin are recorded at UTXO (Unspent Transaction Output)
* BitCoin transactions need to pay transaction fee to those who wrap up the block. As the CoinBase reward is decreasing, the transaction fee might increase in future.  
* Coinbase transaction is one of the transactions in the block merkle tree. It is possible that none of the 32 digit nonce can create a hash value meets the target. In this case, another value can change is the input of the coinbase transaction, which will change the merkle root hash, and finally help tune the block hash value.
 * A transaction in blockchain can't be finally confirmed until it has been included in at least 6 blocks. As the a new block can only be created at the longest valid chain, as long as most of the members are honest, it is very very difficult to finally confirm an illegal transaction (you have to be able to extend the current chain with at least 6 blocks that include your illegal transaction by yourself).
 * Selfish mining: Don't publish the blocks you mined until you have enough blocks to beat the current longest valid chain. It can be a way to accumulate your advantage, but also with the risk to lose all the blocks you have mined.

## BitCoin Network
* The point of BitCoin Network is simple and robust. So when a new transaction is flooded (broadcasted) across the network, any node in the network has the same probability to be notified. The BitCoin network actually sacrifices the efficiency.

## Bitcoin Mining Difficulty
* When mining is too easy, new blocks are created very fast, people might work on too many new blocks at the same time, which separates the computation power of honest nodes. While at the same time a bad node can focus on one bad block and quickly extend it, make a 51% attack work.
* The expected mining time for Bitcoin is one new block per 10 minutes, every two weeks, the mining difficulty is adjusted by target = target * actual_time / expected time. In this formula, actual_time is the actual time spent to generate the last 2016 Bitcoins, the expected time is 2016*10 minutes. So the target will increase if the actual time is bigger than expect time, which makes mining easier (the bigger the target space is, the easier mining will be).

## Mining Details
* ASIC (Application-specific integrated circuit) is the chip specifically designed for mining, while it takes much time to design and the advantage wouldn't last long (a few months). So the cost for mining is very huge.
 * For an individual miner, the probability to mine a block is actually very small. Mining pool was created to organize many miners, which makes the risk for each individual miner much lower.
