# Remote Connection Jupyter Notebook in Azure VM

## Create Virtual Machine - Ubuntu Server 22.04 LTS 
### Basics
1. Set **resource group**
2. Type **Virtual machine name**
3. Select **Region**
4. **Avaibility options**: `Avaibility zone`
5. **Avaibility zone**: choose
6. **Size**: adjust based on the workloads you will have
7. **Authentication type**: `Password`

### Networking
1. In **Virtual network** click `Create new` and type the **Name** of the virtual network
2. **NIC network security group**: `Advance`
3. **Configure network security group**: click `Create new`
4. Then click `+ Add an inbound rule`
5. Change the **Destination port ranges** from `8080` to `8888`
6. In **Protocol** Select `TCP`
7. Click **Add** and then **OK**



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
[hash](https://docs.anaconda.com/free/anaconda/hashes/index.html): c536ddb7b4ba738bddbd4e581b29308cb332fa12ae3fa2cd66814bd735dff231

```bash
bash Anaconda3-2024.02-1-Linux-x86_64.sh
```
- `Enter`
- `yes`
- `enter`
- `yes`

```bash
source ~/.bashrc
```
### Check Conda
```bash
conda list
```

## Set up Conda env
```bash
python3 --version
```

```bash
conda create --name tensorflow python={version}
```

```bash
conda activate tensorflow
```

## Set up source code and datasets
### Clone source code
```bash
git clone `repository_url`
```

### Download dataset using `gdown`
```bash
pip install gdown
```
You may want to read the [Documentation](https://pypi.org/project/gdown/2.3.1/)

```bash
export DRIVE="https://drive.google.com/uc?id="
```

```bash
gdown ${DRIVE}drive_file_id
```
#### Unzip
```bash
sudo apt-get install unzip
```
```bash
unzip *.zip
```

## Set up jupyter notebook
```bash
ssh -L 8080:localhost:8888 {username}@{public_ip}
```
input the password

### Check this syntax in your ipynb file
```bash
jupyter notebook --no-browser
```

```python
# Check the number of CPUs
psutil.cpu_count()
```

```python
# Check virtual memory
psutil.virtual_memory()
```
