# ironfish-scripts

English translation from original Russian readme

ironfish-scripts

The script is run under the bash interpreter.

You can copy the entire root:

git clone https://github.com/kkiplinger/ironfish-scripts.git


Script Function:

1. The script exports and outputs environment variables.

2. Handle changed name of the wallet/graffiti but not changed it in the configs.

3. Request the wallet balance.

4. If it is more than the minimum transaction + commission, then:

	Divide the balance by this number, get the number of possible transactions without re-requesting 
	the balance. Every 10 repetitions, a balance request occurs in the background, but it only affects 
	the display in runtime, so as not to do this in the adjacent console, it does not affect the number 
	of initial repetitions. The script completes its work and repeats the procedure one more time.

Exceptions:

If we see the "Insufficient funds" error, but the global iteration has not completed, then the loop is 
reset, the script waits 5 minutes and starts the loop again. Five such errors and the script will rescan 
the database (takes several hours). This functionality is available at startup with the rescan-allowed 
option. If the script sees an error connecting to the node, then we stop for half an hour and wait for 
it to pass.


To run a standard launch use:

bash ${HOME}/ironfish-scripts/deposit.sh

To run with the rescan database option enabled. Use this for automatic ironfish accounts:rescan. Recommended if you are an advanced user:

bash ${HOME}/ironfish-scripts/deposit.sh rescan-allowed

To Update the script use:

/usr/bin/git -C ${HOME}/ironfish-scripts pull
