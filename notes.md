1.Create minimal Account Abstraction on Ethereum
2. Create minimal Account abstraction zkSync
3. Deploy and send a userOp/transaction through them 
a. Not going to send an AA to Ethereum
b. But we will send an AA transaction to zkSync


alt-mempool nodes
ENV/Entrypoint.sol
your contract

==in a nut shell Our function _validatesSignature verifies the signature of a PackedUserOperation by recovering the signer's address from the hashed OperationData and comparing it with the Owners'address, returning a validation success or failures codes based on the match==For further customization we could verufy that the Google session Key is correct

 1. The purpose of this function is to validate user operations by ensuring that the signature is valid. It also handles missing account funds.

 2. It verifies the signer's address by first converting the `userOpHash` into a signed message hash. It then recovers the signer's address using ECDSA.recover with the signed message hash and the signature from userOp. Finally, it compares the recovered address to the owner's address to determine if the signature is valid.

 3. We need OpenZeppelin's Ownable contract to manage ownership of the contract, ensuring that only the owner can validate signatures.

 4. This function handles the payment of missing account funds owed to the EntryPoint. It checks if there are any missing funds and, if so, pays what is owed.
 
 5. Alt-mempool nodes serve as off-chain relays for user operations. They receive packed user operation objects, validate them (including signature verification), and then relay them to the appropriate on-chain contract for execution.