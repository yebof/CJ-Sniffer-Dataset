# Packet-Level Cryptomining Network Traffic Dataset

This dataset contains labeled, packet-level, cryptomining network traffic generated by both user-initiated cryptomining and illegitimate cryptojacking activities. Here, cryptojacking represents the unauthorized use of someone else's computing resources to mine cryptocurrency. On the other hand, user-initiated cryptomining is the cryptomining performed by legitimate users of computing devices in use.

This dataset is open to public for research purpose only. Information about how to cite this work will be released later. Besides, to protect the rights of authors, a small portion of the data description is temporarily omitted and will be available to the public once we confirm the publication of our paper.

## Data Format
All the cryptomining network traffic are captured in `pcap` format, which means the dataset is in packet-level and contains both headers and payloads of cryptomining messages.
## Labelling Information

- For each collected `pcap` file, we have an entry in the `labels.csv` file to describe its labelling information. The `pcap` file and the corresponding labelling entry are indexed with the same __id__.
- All the entries in the `labels.csv` file follow the same format, with 14 attributes. All the attributes in the `labels.csv` file are described below:
   
    ```
    ID, timestamp, mining_device_config, is_complete, encrypted, hash_rate_1, hash_rate_2, hash_rate_3, submission_number, coin_type, minig_software, algo, whether_cryptojacking, length
    ``` 
    1. __id__: the id of the `pcap` file that this entry describes.
    2. __timestamp__: this field is the timestamp that the mining traffic was cauptured.
    3. __mining_device_config__: describe the computer configuration used for mining. It only contains the hardware that has been utilized. For example, if the miner only uses CPU to mine, then it only records the CPU spec, without the GPU spec.
    4. __is_complete__: should be either `yes` or `no`. Answer `yes` if the traffic contains the registration and logout packets of pool mining. Otherwise, `no`.
    5. __encrypted__: should be either `yes` or `no`. Answer `yes` if the traffic is encrypted. Otherwise, `no`.
    6. __hash_rate_1__: the average hash rate in the latest 10 seconds.
    7. __hash_rate_2__: the average hash rate in the latest 60 seconds.
    8. __hash_rate_3__: the average hash rate in the latest 15 minutes.
    9.  __submission_number__: the number of accepted resuults / the number of rejected results. For example, if the miner submitted 10 mining results and 2 were rejected by the mining pool, this field should be `10/2`
    10. __coin_type__: the type of coin mined in the mining network traffic, in abbreviation (e.g., `xmr`, `eth`, or `btc`).
    11. __minig_software__: the mining software used to conduct mining (e.g., `xmrig`).
    12. __algo__: the algorithms used to conduct mining.
    13. __whether_cryptojacking__: should be either `yes` or `no`. Answer `yes` if any portion of the collected cryptomining traffic is generated by cryptojacking. Otherwise, `no`. *temporarily omitted*
    14. __length__: the length (s) of the collected cryptominig traffic. *temporarily omitted*

## Measures for Ethical Consideration

As the collection of network traffic may cause privacy and other ethical concerns, we take effective measures to address possible ethical considerations. To protect the privacy of users, prevent sensitive information leakage, and ensure that the dataset does not contain any information related to human subject studies, we set rigorous regulations for data collection and preprocessing. We list the regulations below:

1. Before preprocessing, all the raw data is stored on a restricted server. Read and write privileges are only limited to several necessary researchers in this project with PI approvals. This minimizes the risk of accidental leakage of raw network data.
   
2. The IP addresses and port numbers in the network traffic dataset are anonymized. This ensures that people cannot trace back to individuals by analyzing all the `pcap` files.
   
3. We have carefully forged certain fields in the cryptomining packet payload, such as the task ID, hash number, and mining results. This ensures that analyzers cannot dig private information related to the cryptominers from this dataset. Simultaneously, we have kept the source data length, format, characteristics, and patterns unchanged.
   
4. This dataset only contains cryptomining traffic data. Any other background traffic is filtered out.
   
5. This dataset only contains cryptomining traffic data that not impacted by human activities to avoid potential human subject studies based upon this dataset.

## Acknowledgements
This dataset is based upon work supported by Ripple under the University Blockchain Research Initiative (UBRI) program. Any opinions, findings, and conclusions or recommendations expressed in the materials are those of the authors and do not necessarily reflect the views of Ripple.