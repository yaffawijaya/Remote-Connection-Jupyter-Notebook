# Remote Connection Jupyter Notebook in Azure VM

1. Make the VM
2. Config the VM's `Network Security group (firewall)` by adding the inbound rule directed to `8888` Destination port ranges with TCP protocol


## Login to VM by ssh
```bash
ssh {username}@{public_ip}
```

## Set up Anaconda
```bash
cd /tmp && curl -O https://repo.anaconda.com/archive/Anaconda3-2024.02-1-Linux-x86_64.sh
```

```bash
sha256sum Anaconda3-2024.02-1-Linux-x86_64.sh
```
hash: c536ddb7b4ba738bddbd4e581b29308cb332fa12ae3fa2cd66814bd735dff231

```bash
bash Anaconda3-2024.02-1-Linux-x86_64.sh
```
`Enter` `yes` `enter` `yes`

```bash
source ~/.bashrc
```
### Check Conda
```bash
conda list
```

## Set up jupyter notebook
```bash
ssh -L 8080:localhost:8888 {username}@{public_ip}
```
input the password

```bash
jupyter notebook --no-browser
```

```bash

```

```bash

```

```bash

```
