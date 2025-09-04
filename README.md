# pectra-analysis
Post-Pectra Effects on Ethereum: Reorg Rate, Propagation, and Block Size


This repository contains the dataset and Jupyter notebooks used to empirically analyze the impact of the **Pectra hardfork** on Ethereum.  
We focus on how the **reorg rate** changed, how **block and blob propagation times** shifted, and how **block sizes** evolved.  
The analysis connects these outcomes to recent protocol changes, including **EIP-7623**, **EIP-7691**.  

 Clone the repository
```bash
git clone https://github.com/etelpmoc/pectra-analysis.git
cd pectra-analysis
```

Create and activate the conda environment:
```
conda create -n pectra-analysis python=3.11
conda activate pectra-analysis
```

Install required dependencies:
```
pip install -r requirements.txt
```

Launch Jupyter Notebook:
```
jupyter notebook --port 8888
```

Then open your browser and go to: http://localhost:8888

## Data Collection

Data comes from Xatu-data, covering January 1, 2025 – August 27, 2025 (slots #10,738,799 to #12,459,220).
The following tables were used:

Block propagation: libp2p_gossipsub_beacon_block

Blob propagation: beacon_api_eth_v1_events_blob_sidecar

Chain reorgs: beacon_api_eth_v1_events_chain_reorg

Validators: canonical_beacon_validators

Execution blocks & transactions: canonical_execution_block, canonical_execution_transaction

Note: Since beacon_api_eth_v1_events_block_gossip lacks pre-Pectra data, we relied on libp2p_gossipsub_beacon_block for block propagation times. The two sources differ by <10 ms on average, so they are considered closely aligned.
