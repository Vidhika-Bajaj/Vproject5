# Logical gates
This logical gates program takes the inputs as a and b and returns the output as y after passing through the various logical gates that are AND gate and NOT gate.

## Description
This programme is a straightforward example of the operation of a logical AND gate and a NOT gate. It accepts the inputs a and b, processes them through the AND gate to get the output X, then feeds that result into the NOT gate to produce the final output, which is Y. It includes a variety of files, including hardhat.config.ts, gitignore, contracts, scripts, types, and circuits. Hardhat.config.ts has the programme for the Mumbai network along with the relevant url and private key, and dotenv is also installed. Circuits file contains the primary code of the input, output, and their logics depending on the employed gates. The account's private key is also added to the.env file as the network private key, MUMBAIPRIVATEKEY. Additionally, the matic network was introduced to the metamask wallet, enabling matic transactions to occur in the wallet. Mumbai faucet has been utilised for MATIC, but it can only offer matic once every 24 hours, and for that, an account's username and password must be pasted on Mumbai faucet. The Mumbai Testnet is also used to display MATIC transactions.
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
