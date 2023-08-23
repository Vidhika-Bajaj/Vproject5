# Logical gates
This logical gates program takes the inputs as a and b and returns the output as y after passing through the various logical gates that are AND gate and NOT gate.

## Description

This program is a simple program of working of logical AND gate and NOT gate that takes the input as a and b then passes through the And gate and returns the output as X, then that output X of AND gate taken as an input of the NOT gate and then the final output get recieved as Y. It contains various files such as circuits, contracts, scripts, types, hardhat.config.ts, gitignore, etc. circuits file contains the main code of input, output and their logics based on the used gates, hardhat.config.ts contains the program for mumbai network and the related url and private key, also the dotenv is get installed. Private key of the account is also get included in .env file as network private key i.e. MUMBAIPRIVATEKEY. Also in metamask wallet, matic network got added through which the matic transaction can take place in wallet. For MATIC, mumbai faucet has been used but it can provide matic only once in 24 hrs and for that account's has to be pasted on mumbai faucet. Also mumbai testnet is used for showing the transactions of MATIC.

## Getting Started
### Executing program
       
```javascript
pragma circom 2.0.0;

/*This circuit template checks that c is the multiplication of a and b.*/  

template Multiplier2 () {  

   // signal inputs
   signal input a;
   signal input b;

   // signals from gates
   signal x;

   // final signal output
   signal output y;

   // component gates used to create custom circuit
   component andGate = AND();
   component notGate = NOT();

   // circuit logic
   andGate.a <== a;
   andGate.b <== b;
   x <== andGate.out;

   notGate.in <== x;
   y <== notGate.out;
 
}

template AND() {
    signal input a;
    signal input b;
    signal output out;

    out <== a*b;
}

template NOT() {
    signal input in;
    signal output out;

    out <== 1 + in - 2*in;
}

component main = Multiplier2();                          
```
To compile the code, various commands have to be executed sequentially in the terminal that is-
1. npm i
2. npx hardhat circom
3. npx hardhat run scripts/deploy.ts

Also for install and setting up dotenv:
1. npm install dotenv --save

Once the code is compiled, MATIC can be transact from mumbai faucet to wallet.

## Authors
Vidhika Bajaj

## License
This project is licensed under the MIT License
