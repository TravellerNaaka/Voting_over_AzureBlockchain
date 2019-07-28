# Voting_over_AzureBlockchain
We want an electronic voting system using blockchain that is a secure and robust system that ensures anonymity of the voter, is transparent in it’s working, and has robust functioning.

We introduce a trusted third party (TTP) into the blockchain network which would enable voter anonymity. 
The blockchain network would comprise of all the voters (those already issued with voter IDs) as ordinary nodes, verified by the Election Commission of India (ECI). 
The candidates would be also as ordinary nodes with valid voter ID’s, which, through a nomination process can become Candidate Nodes. Some nodes with special privileges, like the UIDAI ( Aadhar issuing agency in India ), Election Commission of India ( ECI )  would be present along with the TTP. 
A smart contract would be published on Azure Blockchain, which would check if a person is eligible to get his voter ID issued if not yet issued i.e hold an Aadhar ID.

Each day, say at 2 AM in the morning, UIDAI broadcasts 2 input streams on the network ( ordinary nodes like voters have nothing to do with these streams ). One of these would be the data of all the existing Aadhar card holders who just turned 18 the previous day ( could be filtered out using a simple script from UIDAI database ). Other stream would be the data pertaining to all the new entrants in its database ( who got their Aadhar Card issued just yesterday, also filtered for 18 + age criteria). These 2 data streams would be broadcasted on the network, and a smart contract ( implemented between UIDAI and ECI ) would operate on the data streams.

The contract would re-check for each individual entry in the streams for age to confirm a value of 18+. Also, for each data entry, the contract would search through the existing voter database of ECI to look for identical entries in that database. This is a provision for entries from stream 2, where a person who is 18+ and already holds a voterID, got his Aadhar issued just yesterday. His information has also been broadcasted by UIDAI on the network. But, he must not be issued another VoterID, to prevent the problem of double-voting.

If the smart contract verifies that a data-entry broadcasted has an age field with a value of 18+, and its data is unique from all the existing voter database available with ECI, then ECI should be directed to issue him a voterID. Only after that person is issued a voterID and is made another node on the existing network, the contract is deemed accomplished.

This solves the problem of creating a voterID immediately as a person turns 18. Also, it solves the problem of issuing multiple IDs for existing voters who apply for an Aadhar after getting the voterID issued. We want to mention that the design of this solution is India specific, as India has a sophisticated nationwide unique identification database in the form of Aadhar.

Voting Process:
Person X declares intention to vote on the ECI website and submits his VoterID.
If eligible, X will be asked to submit a secret message. Once submitting a secret message, X will receive a unique reference number along with the secret message. In the process, John should not reveal the secret message or reference number to anyone.

To vote, X goes to TTP and submits secret message and reference number to vote.
TTP determines if the hash of the secret message and the reference number is present in ECI database. Upon confirmation, X is allowed to go to the page where he can vote for candidates that belong to his constituency. During this phase, TTP generates a public address for X in blockchain and stores this against the voter public address in its database.

If X tries to vote for the same candidate or any other candidate by entering his secret message and reference number, TTP will check if voter IDash is already present in its database. If it’s present, it means that X is trying to vote for the second time and the system will prevent that.

!(C:\Users\kanav\Pictures\Screenshots)
