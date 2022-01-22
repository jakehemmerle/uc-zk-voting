# Part I. Description of Overall Test Plan



# Part II. Test Case Descriptions

List a series of 10-25 tests for validating your project outcomes. For each test case provide the following:
1. test case identifier (a number or unique name)
2. purpose of test
3. description of test
4. inputs used for test
5. expected outputs/results
6. normal/abnormal/boundary case indication
7. blackbox/whitebox test indication
8. functional/performance test indication
9. unit/integration test indication
Note that some of these categories may be inappropriate for your project and may be omitted if you can justify doing so. For items 6-9, only one term should apply.

## Voting Process Tests (VP)
### VP1. Begin voting process
- T1.2 Ensure that we can successfully begin the voting process
- T1.3 This test will call a function in our module to start the voting process. We will then need to check that change was made on-chain to reflect a successful execution of said function.
- T1.4 Inputs: Blockheight for voting duration, identify operator ?????
- T1.5 Output: New block added signifying the beginning of the voting process
- T1.6 Normal
- T1.7 Blackbox
- T1.8 Functional
- T1.9 Integration

### VP2. Voting stops (block height)
- T1.2 Ensure that the voting process stops once a predefined block height is met
- T1.3 After the voting process has already begun, we will know the block height that the voting should stop at. Once that block height is met we expect to see a change made on-chain to show that voting can no longer continue.
- T1.4 Inputs: Nothing?
- T1.5 Output: New block?
- T1.6 Normal
- T1.7 Blackbox
- T1.8 Functional
- T1.9 Integration

### VP3. Voting results posted
- T1.2 Ensure that the results of the voting process are visible to users
- T1.3 Once the predetermined block height is met and the voting has stopped, we expect to see the results of the voting process to be posted shortly after.
- T1.4 Inputs: Nothing?
- T1.5 Output: New block?
- T1.6 Normal
- T1.7 {blackbox/whitebox test indication}
- T1.8 Functional
- T1.9 Integration

### VP4. Initialize an Operator (predetermined, key is shared publically)
- T1.2 {purpose}
- T1.3 {description}
- T1.4 Inputs: 
- T1.5 Output: 
- T1.6 {normal/abnormal/boundary case indication}
- T1.7 {blackbox/whitebox test indication}
- T1.8 {functional/performance test indication}
- T1.9 {unit/integration test indication}

## Sybil Resistance Mechanism Tests (SR)

### SR1. Whitelist (Pre-existing addresses)
- T1.2 Ensure that a whitelist has been properly established
- T1.3 With whitelist parameters setup, as a whitelisted user we should not be required to sign up to vote. We will check this by looking at the whitelisted users after the voting process starts and ensure the list is correct.
- T1.4 Inputs: ?
- T1.5 Output: ?
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Integration

## User Capabilities Tests (UC)

### UC1. Sign up
- T1.2 Ensure that a user is added to the state tree after they sign up.
- T1.3 We will test the sign up function by calling it as a user not currently signed up, and then check that said user was added to the internal state tree and is allowed to vote.
- T1.4 Inputs: ?
- T1.5 Output: Nothing
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Integration

### UC2. Change keys
- T1.2 Ensure that the voting operator properly handles a change key request
- T1.3 As a signed up user we will call the change keys function and ensure that we are given a new set of keys unique from the ones we already have. Then we will check that the operator has updated the state tree and the message tree with these changes.
- T1.4 Inputs: Nothing
- T1.5 Output: New keys
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Integration

### UC3. Vote (valid)
- T1.2 Ensure that a vote from a valid user is properly registered
- T1.3 As a signed up user we will call the vote function with our valid keys. Then we will check that this vote was added to the message tree
- T1.4 Inputs: Cryptographically signed message
- T1.5 Output: ??
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit

### UC4. Vote (invalid)
- T1.2 Ensure that a vote from a invalid user is properly registered
- T1.3 As a signed up user we will call the vote function with an invalid set of keys. Then we will check that the vote was added to the message tree
- T1.4 Inputs: Cryptographicall signed message
- T1.5 Output: ??
- T1.6 Normal
- T1.7 Whitebox
- T1.8 Functional
- T1.9 Unit


## System Tests (SYS)
### SYS1. Stale votes ignored (voting with old key)
- T1.2 {purpose}
- T1.3 Make a vote on entity 1, change keys as that user, make a vote on entity 2, ensure only the second vote was counted.
- T1.4 Inputs: 
- T1.5 Output: 
- T1.6 {normal/abnormal/boundary case indication}
- T1.7 {blackbox/whitebox test indication}
- T1.8 {functional/performance test indication}
- T1.9 {unit/integration test indication}

### SYS2. Voting with another users key doesn't work
- T1.2 {purpose}
- T1.3 {description}
- T1.4 Inputs: 
- T1.5 Output: 
- T1.6 {normal/abnormal/boundary case indication}
- T1.7 {blackbox/whitebox test indication}
- T1.8 {functional/performance test indication}
- T1.9 {unit/integration test indication}

## Crypto Tests (CO)

### CO1. ECDH works for generating shared key
- T1.2 {purpose}
- T1.3 {description}
- T1.4 Inputs: 
- T1.5 Output: 
- T1.6 {normal/abnormal/boundary case indication}
- T1.7 {blackbox/whitebox test indication}
- T1.8 {functional/performance test indication}
- T1.9 {unit/integration test indication}

### CO2. Voting result proofs works
- T1.2 {purpose}
- T1.3 {description}
- T1.4 Inputs: 
- T1.5 Output: 
- T1.6 {normal/abnormal/boundary case indication}
- T1.7 {blackbox/whitebox test indication}
- T1.8 {functional/performance test indication}
- T1.9 {unit/integration test indication}


# Part III. Test Case Matrix

Test Case Matrix: summarizes the test case coverage (items 1, 6-9 in a tabular format)

yellow box:  
             