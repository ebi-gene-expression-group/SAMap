# SAMap -- version 0.1.4
The SAMap algorithm.

# Beta
Hello! Just a friendly reminder that if any of you have trouble getting SAMap up and running or want to know more about the various arguments, please do not hesitate to reach out to me by submitting an issue!

## Requirements
SAMap was developed and tested in an Anaconda python environment with the following dependencies:
 - `sam-algorithm`
 - `scanpy`
 - `hnswlib`

## Installation

### Manual installation
Download Anacodna from here:
    https://www.anaconda.com/download/

Create and activate a new environment for SAMap as follows:

```bash
# Install SAMap dependencies availabe in conda
conda create -n SAMap -c conda-forge python=3.7 pip pybind11 h5py=2.10.0 leidenalg python-igraph texttable
conda activate SAMap
```

Having activated the environment, install SAMap like so:


```bash
git clone https://github.com/atarashansky/SAMap.git samap_directory
cd samap_directory
pip install .
```

NCBI BLAST must be installed for the commandline.

```bash
# Define NCBI BLAST version.
ncbi_blast_version='2.9.0'

# Download NCBI BLAST tarball.
wget "ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/${ncbi_blast_version}/ncbi-blast-${ncbi_blast_version}+-x64-linux.tar.gz"

# Extract NCBI BLAST binaries in current conda environment bin directory.
tar -xzvf "ncbi-blast-${ncbi_blast_version}+-x64-linux.tar.gz" \
    -C "${CONDA_PREFIX}/bin/" \
    --strip-components=2 \
    "ncbi-blast-${ncbi_blast_version}+/bin/"
```

Alternatively, add the NCBI BLAST binaries manually to the path:

```bash
# Define NCBI BLAST version.
ncbi_blast_version='2.9.0'

# Download NCBI BLAST tarball.
wget "ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/${ncbi_blast_version}/ncbi-blast-${ncbi_blast_version}+-x64-linux.tar.gz"

# Extract NCBI BLAST tarball.
tar -xzvf "ncbi-blast-${ncbi_blast_version}+-x64-linux.tar.gz"

# Add NCBI BLAST programs to PATH.
echo "export PATH=\"$PATH:/your/directory/ncbi-blast-${ncbi_blast_version}+/bin\"" >> ~/.bashrc
source ~/.bashrc
```

### Dockerfile installation
Assumes Docker is installed on your computer.

Run `bash build_image.sh` to build the Docker image.

Run `bash run_image.sh` to run the Docker image.

Running the Docker image will spawn a jupyter notebook server on your specified port.

*Installation time should take no more than 5 minutes.*

## Running BLAST

The BLAST mapping script can be run from the `SAMap_quickstart.ipynb` Jupyter notebook.

Depending on the number of cores available on your machine and the size/type of the input fasta files, this step may take up to around 4 hours.

## Running SAMap

To run SAMap, use the `SAMAP` function in `samap/mapping.py`. Please see its function documentation for a description of the inputs and outputs. Take a look at the provided Jupyter notebook to get started (`SAMap_quickstart.ipynb`).
