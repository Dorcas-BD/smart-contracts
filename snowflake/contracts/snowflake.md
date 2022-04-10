# Snowflakes.sol Contract Review
Code Review
 The snowflakes contract aim is an identity management protocol

This snowflake contract inherits the Ownable contract ``` contract Snowflake is Ownable ```. This helps to associate ownership to the contract and helps to control who gets to call the function.

**Line 16-18** The first mapping is the mapping of **EIN**(Ethereum Identification Number) to the amount of hydrogen token deposited.
The second mapping is a nested mapping whhich maps EIN from the Resolver address to the allowances. 

**Line 21-26** declares the state variables and the interfaces 

**Line 28-30:** is declaring a signature state variables and mapping it to the signatureNounce identifier 

**Line 31-34:** The constructor is accepting the identityRegistryAddress and the hydroTokenAddress as a parameters 

### ```identityExists```  and ```ensureSignatureTimeValid``` modifiers
These are the two modifiers in this contract. ```identityExists``` ensures that a particular EIN exist. ``` require(identityRegistry.identityExists(ein) == check, "The EIN does not exist."); ```. It require to check the EIN input parameters in the **identityRegistry**(__identity registry is the place where all the identies are labeled by EIN__) if it exists. The other modifier ```ensureSignatureTimeValid``` is to verify if the timestamp is valid.

### ```setAddresses``` function
The first function of this contract is the function which accept the _identityRegistryAddress and the _hydroTokenAddress as parameters and assigned it to the IdentityRegistryInterface and the HydroInterface.

### ```setClientRaindropAddress``` function
The second function can be called by only the owner of the contract. It accept ```_clientRaindropAddress``` as parameter and set it as ```ClientRaindropInterface``` address.


### ```createIdentityDelegated``` function
The function is called by the provider and it requires signature to confirm the associatedAddress. This function also add new EIN to the identityRegistry. The ```_addResolver``` add an array of Resolver to the EIN and it must be called by a Provider.


### ```addProvidersFor``` function
The function adds the arrays of Provider reference by the approvingAddress. This function requires the timestamp ```approvingAddress``` signed it before it's added to the ```identityRegistry```. The ```getEIN``` verify the EIN is associated with the input address(that is the **approvingAddress**)


### ```removeProviderFor``` function
The funtion from **line 114-136**. This function is the same with the ```addProviderFor``` function. Just that it remove he Provider.


### ```upgradeProvidersFor``` function
This function gives permision to ```addProviderFor``` and ```removeProviderFor``` by signature. It verify the EIN of the approvingAddress and call the ```SnowflakeProvidersUpgraded``` event to make the upgrade.


### ```addResolver``` function
The ```addResolver``` function add a resolver for identity of msg.sender. Resolver helps to resolve abstract data in smart contract to an identity.


### ```addResolverAsProvider``` function
This function is the same as ```addResolver``` function just that it is passed by a provider.


### ```addResolverFor``` function
This function function perform the same logic as the ```addResolver``` but must be called by a Provider.


### ```validateAddResolverForSignature``` function
This is a private function that ensure that the signature time is valid by calling the *ensureSignatureTimeValid* modifier. This function is called by the Provider to make sure the he authorised the adding the resolver to the identity.


### ```_addResolver``` function
This function is the logic use to add new resolvers. This is a proivate function that take the EIN, resolver address as a parameters and also check if the EIN and resolver address does not exist in the identityRegistry before adding the resolver. Also, the function check if it has Snowflakes to allow withdrawal.


### ```changeResolverAllowances``` function
It change resolver allowances for identity of msg.sender.


### ```changeResolverAllowancesDelegated``` function
### ```changeResolverAllowances``` function
### ```removeResolver``` function
### ```removeResolverFor``` function
### ```validateRemoveResolverForSignature``` function
### ```removeResolver``` function
### ```triggerRecoveryAddressChangeFor``` function
### ```receiveApproval``` function
### ```transferSnowflakeBalance``` function
### ```withdrawSnowflakeBalance``` function
### ```transferSnowflakeBalanceFrom``` function
### ```withdrawSnowflakeBalanceFrom``` function
### ```transferSnowflakeBalanceFromVia``` function
### ```withdrawSnowflakeBalanceFromVia``` function
### ``` _transfer``` function
### ```_withdraw``` function
### ```handleAllowance``` function
### ```allowAndCall``` function
### ```allowAndCallDelegated``` function
### ```validateAllowAndCallDelegatedSignature``` function
### ```allowAndCall``` function
### ```SnowflakeProvidersUpgraded``` event
### ```SnowflakeResolverAdded``` event
### ```SnowflakeResolverAllowanceChanged``` event
### ```SnowflakeResolverRemoved``` event
### ```SnowflakeDeposit``` event
### ```SnowflakeTransfer``` event
### ```SnowflakeWithdraw``` event
### ```SnowflakeTransferFrom``` event
### ```SnowflakeTransferFromVia``` event
### ```SnowflakeWithdrawFromVia``` event
### ```SnowflakeTransferToVia``` event
### ```SnowflakeWithdrawToVia``` event
### ```SnowflakeInsufficientAllowance``` event
### ```SnowflakeBalanceBurnt``` event
