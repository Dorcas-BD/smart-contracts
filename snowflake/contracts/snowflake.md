# Snowflakes Contract Review
Code Review
 The snowflakes contract aim is for identification, verification and protection of users privacy.

This snowflake contract inherits the Ownable contract. This helps to associate ownership to the contract and helps to control who gets to call the function.

The mapping of EIN to the amount of hydrogen token deposited
The second nested mapping is mapping EIN from the Resolver address to the allowances. 

**Line 21-26** declares the state variables and the interfaces 

**Line 28-30:** is declaring a signature state variables and mapping it to the signatureNounce identifier 

**Line 31-34:** The constructor is accepting the identityRegistryAddress and the hydroTokenAddress as a parameters 

There are two modifiers in this contract from **line 37-49** One ensures that a particular EIN exist and the other verify the timestamp is valid.

