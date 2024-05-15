# Remote Connection Jupyter Notebook in Azure VM

1. Make the Virtual Machine in Azure
2. Config the VM's `Network Security group (firewall)` by adding the inbound rule directed to `8888` Destination port ranges with `TCP` protocol


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
git clone https://github.com/Dimitri2801/Cataract-Detection-MobileNetV2.git
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

## Set up jupyter notebook
```bash
ssh -L 8080:localhost:8888 {username}@{public_ip}
```
input the password

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
