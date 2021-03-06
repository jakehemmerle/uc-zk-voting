# Part I. Description of Overall Test Plan
We are trying to complete a comprehensive testing plan. The idea is to first test the voting process from an outside perspective. Make sure that a user implementing our module can use the functions properly. Afterwards we want to move forward and test that the internal state is kept properly. Using that, we will ensure that the system can not be taken advantage of and used for malicious purposes.

# Part II. Test Case Descriptions
## Voting Process Tests (VP)

### VP1. Begin voting process

- T1.2 Ensure that we can successfully begin the voting process
- T1.3 This test will call a function in our module to start the voting process. We will then need to check that change was made on-chain to reflect a successful execution of said function.
- T1.4 Inputs: Blockheight for voting duration, identify operator
- T1.5 Output: New voting session (new tx on-chain)
- T1.6 Normal
- T1.7 Blackbox
- T1.8 Functional
- T1.9 Integration

### VP2. Voting stops (block height)

- T1.2 Ensure that the voting process stops once a predefined block height is met
- T1.3 After the voting process has already begun, we will know the block height that the voting should stop at. Once that block height is met we expect to see a change made on-chain to show that voting can no longer continue.
- T1.4 Inputs: previously defined block height
- T1.5 Output: results
- T1.6 Normal
- T1.7 Blackbox
- T1.8 Functional
- T1.9 Integration

### VP3. Voting results posted

- T1.2 Ensure that the results of the voting process are visible to users
- T1.3 Once the predetermined block height is met and the voting has stopped, we expect to see the results of the voting process to be posted shortly after.
- T1.4 Inputs: null
- T1.5 Output: voting results
- T1.6 Normal
- T1.7 blackbox
- T1.8 Functional
- T1.9 Integration

### VP4. Initialize an Operator (predetermined, key is shared publically)

- T1.2 Allows for anti-collusion
- T1.3 Make sure operator can process votes
- T1.4 Inputs: cryptographic randomness for their key
- T1.5 Output: a working operator
- T1.6 Normal
- T1.7 Blackbox
- T1.8 functional
- T1.9 integration

## Sybil Resistance Mechanism Tests (SR)

### SR1. Whitelist (Pre-existing addresses)

- T1.2 Ensure that a whitelist has been properly established
- T1.3 With whitelist parameters setup, as a whitelisted user we should not be required to sign up to vote. We will check this by looking at the whitelisted users after the voting process starts and ensure the list is correct.
- T1.4 Inputs: Input list of SS58 addresses
- T1.5 Output: Addresses should be visible on-chain
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Integration

## User Capabilities Tests (UC)

### UC1. Sign up

- T1.2 Ensure that a user is added to the state tree after they sign up.
- T1.3 We will test the sign up function by calling it as a user not currently signed up, and then check that said user was added to the internal state tree and is allowed to vote.
- T1.4 Inputs: address
- T1.5 Output: valid voter state change
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Integration

### UC2. Change keys

- T1.2 Ensure that the voting operator properly handles a change key request
- T1.3 As a signed up user we will call the change keys function and ensure that we are given a new set of keys unique from the ones we already have. Then we will check that the operator has updated the state tree and the message tree with these changes.
- T1.4 Inputs: new keys
- T1.5 Output: operator sees keychange
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Integration

### UC3. Vote (valid)

- T1.2 Ensure that a vote from a valid user is properly registered
- T1.3 As a signed up user we will call the vote function with our valid keys. Then we will check that this vote was added to the message tree
- T1.4 Inputs: signed vote, pub pub key
- T1.5 Output: valid vote
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit

### UC4. Vote (invalid)

- T1.2 Ensure that a vote from a invalid user is properly registered
- T1.3 As a signed up user we will call the vote function with an invalid set of keys. Then we will check that the vote was added to the message tree
- T1.4 Inputs: signed vote, wrong pubkey
- T1.5 Output: invalid vote
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit


## System Tests (SYS) (Brandon)
### SYS1. Stale votes ignored (voting with old key)
- T1.2 Ensure that a vote from an old key is not counted
- T1.3 Make a vote on entity 1, change keys as that user, make a vote on entity 2, ensure only the second vote was counted.
- T1.4 Inputs: Cryptographically signed message with an old key
- T1.5 Output: Voting results with the vote not counted
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit

### SYS2. Voting with another users key doesn't work
- T1.2 Edge case to prevent malicious activity
- T1.3 Ensure that if a user knows another users key they can't vote on their behalf
- T1.4 Inputs: pubkey1, signature from pubkey2
- T1.5 Output: invalid vote result
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit

## Crypto Tests (CO) (Jake)

### CO1. ECDH works for generating shared key

- T1.2 Make sure voters and operator can commuincate
- T1.3 Generates a shared key for the voter and operator to communicate
- T1.4 Inputs: cryptographic randomness for keygen, keypairs from voter and operator
- T1.5 Output: shared keys match
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit test

### CO2. Voting result proofs works

- T1.2 Allows voting to happen
- T1.3 Test the proofs to make sure we can make a proof SNARK from them
- T1.4 Inputs: message tree
- T1.5 Output: valid result, proof, and state
- T1.6 Normal
- T1.7 Blackbox
- T1.8 Functional
- T1.9 Integration test

# Part III. Test Case Matrix

|Test Case Identifier | normal/abnormal/boundary case | blackbox/whitebox test | functional/performance test | unit/integration test | completion |
|--------------|--------------|-----------------|--------------------|---------------|---------------|
| VP1 | normal | blackbox | functional | integration | :white_check_mark: |
| VP2 | normal | blackbox | functional | integration | :white_check_mark: |
| VP3 | normal | blackbox | functional | integration | :white_check_mark: |
| VP4 | normal | blackbox | functional | integration | :white_check_mark: |
| SR1 | normal | whitebox | functional | integration |  |
| UC1 | normal | whitebox | functional | integration |  |
| UC2 | normal | whitebox | functional | integration |  |
| UC3 | normal | whitebox | functional | unit | :white_check_mark: |
| UC4 | normal | whitebox | functional | unit |  |
| SYS1 | normal | whitebox | functional | unit |  |
| SYS1 | normal | whitebox | functional | unit |  |
| CO1 | normal | whitebox | functional | unit |  |
| CO2 | normal | whitebox | functional | integration |  |

Note: Due to the project re-work in January 2022, which was approved by our project advisor, a lot of the advanced functionality required for a production ready pallet were not implemented due to time restrictions. Features such as User Signup and Sybil Resistance were put off in favor of completing the Voting Process and implementation of the data structures. This allowed us to finish the project in time for our demonstrations in April 2022.
