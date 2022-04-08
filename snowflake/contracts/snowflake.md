# Snowflakes Contract Review
Code Review
 The snowflakes contract aim is an identity management protocol

This snowflake contract inherits the Ownable contract. ``` contract Snowflake is Ownable ```. This helps to associate ownership to the contract and helps to control who gets to call the function.

**Line 16-18** The first mapping is the mapping of **EIN**(Ethereum Identification Number) to the amount of hydrogen token deposited.
The second mapping is a nested mapping whhich maps EIN from the Resolver address to the allowances. 

**Line 21-26** declares the state variables and the interfaces 

**Line 28-30:** is declaring a signature state variables and mapping it to the signatureNounce identifier 

**Line 31-34:** The constructor is accepting the identityRegistryAddress and the hydroTokenAddress as a parameters 

There are two modifiers in this contract from **line 37-49** One ensures that a particular EIN exist. ``` require(identityRegistry.identityExists(ein) == check, "The EIN does not exist."); ```. It require to check the EIN input parameters in the **identityRegistry**(__identity registry is the place where all the identies are labeled by EIN__) if it exists. The other modifier is to verify if the timestamp is valid.

The first function of this contract is the ``` **__setAddresses__** ``` function which accept the _identityRegistryAddress and the _hydroTokenAddress as parameters and assigned it to the IdentityRegistryInterface and the HydroInterface.

The second function ```setClientRaindropAddress``` can be called by only the owner of the contract. It accept ```_clientRaindropAddress``` as parameter and set it as ```ClientRaindropInterface``` address.

The ```createIdentityDelegated``` function is called by the provider and it requires signature