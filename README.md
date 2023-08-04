# valinor-rawdata
Raw Redis datasets containing the measurement results of Valinor NSDI '23 paper

## Getting Started
The dataset is stored in Zenodo and can be accessed in two ways:

1. Direct Webpage access via: [https://zenodo.org/record/8212701](https://zenodo.org/record/8212701). You can use your web browser to download the files.

2. Using zenodo-get in Python:
```bash
pip3 install zenodo-get
./.local/bin/zenodo_get https://zenodo.org/record/8212701
```
Zenodo_get also provides other useful flags!

## File Naming convention
Unfortunately, we were limited to 50GB of data in Zenodo, therefore we chose part of the datasets we used in our paper. We will update this section with the experiment/workload description for each file.

## File format
All the stored files are in `rdb` format. Please refer to the `load_redis.sh` script provided in [valinor-o](https://github.com/hopnets/valinor-o) repository for an example of how to load rdb files. Alternatively, you can rename the file to 'dump.rdb' and copy it to Redis working directory. After restarting Redis, it will automatically load the database from the file.

The data is formatted as Redis sorted sets. Each file contains various keys (1-10) that belong to different host networking configurations. Each key will contain thousands to millions of Valinor timestamp records. Please refer to Valinor-o repository for more information on how to parse the values from Redis datasets.

Each value contains the following information for every packet:
- Flow 4 tuple
- packet length
- Arrival timestamp at switch Ingress pipeline
- Arrival timestamp at switch traffic manager
- Queueing delay at the switch.

## Citation info
If you find the dataset useful, please cite our paper:
```
@inproceedings{valinor,
  title={Understanding the impact of host networking elements on traffic bursts},
  author={Sharafzadeh, Erfan and Abdous, Sepehr and Ghorbani, Soudeh},
  booktitle={20th USENIX Symposium on Networked Systems Design and Implementation (NSDI 23)},
  pages={237--254},
  year={2023}
}
```
