# SuperMeshNet

This is the official implementation of the ICML 2026 paper:

**Semi-Supervised Neural Super-Resolution for Mesh-Based Simulations**  
Jiyeon Kim, Youngjoon Hong, and Won-Yong Shin  
*Proceedings of the 43rd International Conference on Machine Learning (ICML 2026)*

## Data Preparation

We provide three FEM datasets:
- **Dataset 1:** `data_angle`
- **Dataset 2:** `data_geometry`
- **Dataset 3:** `data_poisson`

You can either **download the FEM datasets** or **generate them from scratch**.

We also provide three CFD datasets:
- **Real-world geometry dataset:** `data_bike`
- **Time-dependent PDE dataset1:** `data_cylinder`
- **Time-dependent PDE dataset2:** `cfd32.npy` `cfd1024.npy` 

You can **download the CFD datasets** 


### Option 1: Download datasets
Download the pre-generated datasets from:
https://drive.google.com/drive/folders/1jl6zad3mMQDrRwnOhryzJl6R8R8dK3wM?usp=sharing

After downloading, unzip the files and place them in your `data/` directory.

### Option 2: Generate datasets
1. Create a new conda environment and install **FEniCSx** (e.g., version 0.10.0):  
   https://fenicsproject.org/download/
2. Run the corresponding notebooks:
   - `data_angle.ipynb` → Dataset 1
   - `data_geometry.ipynb` → Dataset 2
   - `data_poisson.ipynb` → Dataset 3

### Data Directory Structure

```
data/
├── data_angle/
├── data_geometry/
├── data_poisson/
├── data_bike/
├── data_cylinder/
├── cfd32.npy
└── cfd1024.npy
```

---

## Installation Tips

1. Create a conda environment.

2. Install PyTorch Geometric and its dependencies.  
   Make sure to match the **PyTorch and CUDA versions**.

```bash
pip install torch_geometric -f https://data.pyg.org/whl/torch-2.2.0+cu118.html
pip install torch_cluster torch_scatter torch_sparse torch_spline_conv \
    -f https://data.pyg.org/whl/torch-2.2.2+cu118.html
```

3. Install PyTorch and related packages (refer to installing previous versions of Pytorch page [https://pytorch.org/get-started/previous-versions/](https://pytorch.org/get-started/previous-versions/)):

```bash
pip install torch==2.2.2 torchvision==0.17.2 torchaudio==2.2.2 \
    --index-url https://download.pytorch.org/whl/cu118
```

4. Use **NumPy 1.x**:

```bash
pip install numpy==1.26.3
```

5. Install additional dependencies:

```bash
pip install joblib matplotlib scikit-learn
```

6. Install pytorch3d

```bash
conda install -c iopath iopath
conda install pytorch3d -c pytorch3d
```
If `pytorch3d` installation fails, use  
   `torch_geometric.nn.knn_interpolate` instead of the custom implementation in  
   `utils/knn_interpolate.py`.

---

## Main Dependencies

- Python 3.9.19  
- NumPy 1.26.3  
- PyTorch 2.2.2  
- Torchaudio 2.2.2  
- Torchvision 0.17.2  
- torch_cluster 1.6.3  
- torch-geometric 2.6.1  
- torch_scatter 2.1.2  
- torch_sparse 0.6.18  
- torch_spline_conv 1.2.2  
- pytorch3d 0.7.8  
- scikit-learn  
- matplotlib  
- joblib  

---

## Usage


### FEM datasets
For GCN and GAT (only node-level centering is available), refer to the notebook:

```
notebooks/GCN_angle.ipynb
```

For SAGE, GTR, GIN, MGN (both node-level and edge-level centerins are avialbe), refer to the notebook:

```
notebooks/MGN_angle.ipynb
```

### CFD datasets
For Real-world geometry dataset, refer to the notebook: 

```
notebooks/MGN_bike.ipynb
```

For Time-dependent PDE dataset 1, refer to the notebook:

```
notebooks/MGN_cylinder.ipynb
```

For Time-dependent PDE dataset 2, refer to the notebook:

```
notebooks/MGN_cfd.ipynb
```