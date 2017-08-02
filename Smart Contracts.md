
### Data Structures

* Pandora Contract
	- Kernel contracts
	- Dataset contracts
	- Worker nodes contracts
* Kernel contract
	- IPFS file for kernel config (containing references to files with weights and models)
	- beneficiary address
	- computational complexity info
	- compatibility info
	- input data dimensions
* Dataset contract
	- IPFS file for dataset
	- number of data records

```sequence
Kernel author->Pandora Contract: New kernel data
Pandora Contract->Kernel Contract: Init
Kernel Contract-->Pandora Contract: Save contract address
```

```sequence
Client->Client Software:Browse kernels
Client Software->>Pandora Contract:Data exchange via web3
Pandora Contract-->>Client Software:
Note left of Client:Kernel selected
Client->Client Software:Browse datasets
Client Software->>Pandora Contract:Data exchange via web3
Pandora Contract-->>Client Software:
Note left of Client:Dataset selected
Client->Client Software:Make order
Client Software->Pandora Contract:Deposit PAN tokens
Client Software->Pandora Contract:Setup contract
Pandora Contract->Computations Contract:Init
Pandora Contract->Computations Contract:Deposit PAN tokens
Computations Contract->>Worker Nodes:Event-triggerend computations
```

Questions:

* do we need separate contracts for kernels and datasets or just data structures?
* do we need separate contracts for working nodes