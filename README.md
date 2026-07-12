# pathSQE

The pathSQE software automates the analysis of single-crystal inelastic neutron scattering datasets collected with time-of-flight instruments. It integrates with Mantid's python API and enables systematic slicing, symmetrization, and visualization of data in reciprocal space, facilitating the exploration of large wavevector–energy volumes and comparisons with theoretical predictions.

## Getting Started

### 0. Detailed description

A detailed description of the capabilities and implementation of pathSQE can be found in the paper. Link and file. 

### 1. Clone the repository

On any system with Git installed:

```bash
git clone https://github.com/delaire-lab-duke/pathSQE.git
```

Alternatively, one can download and transfer the repository as a ZIP file.

---

### 2. Set up the environment

The software requires relatively few packages to run. Basic environmental setup instructions using Pixi or Conda are provided below.

#### Pixi (suggested)

If Pixi is installed system-wide, as is the case on the ORNL SNS analysis cluster, one can effectively skip this step since the pixi.toml file is provided. Running the code using the pixi run command (in step 5) automatically prepares and uses the correct python environment.

#### Conda
For full functionality including phonon simulations, create a conda environment:

```bash
conda create -n pathSQE -c conda-forge -c mantid mantid phonopy
conda activate pathSQE
```

For experimental data analysis (no simulations required):

```bash
conda create -n mantid -c mantid mantid
conda activate mantid
```


---

### 3. Specify your dataset

Edit `define_data.py` to point to the target experimental data.

If run as-is on the ORNL SNS analysis cluster, the provided version works out-of-the-box with a publicly available single-crystal Si dataset measured at 300 K on ARCS at the SNS.

---

### 4. Set analysis parameters

Edit `pathSQE_input.py` to configure the desired slicing paths, symmetry settings, and output options.

---

### 5. Run the workflow

From a terminal, run:

```bash
pixi run python pathSQE_driver.py
```

Or if using conda, with the environment active run:

```bash
python pathSQE_driver.py
```

---

## Example Output

An example of a symmetrized, folded \( I(\mathbf{q}, E) \) from the publicly available Si dataset at 300 K:

![Example 300K Si folded I(Q,E)](examples/Si_ARCS_publicData/folded_path_plot_106.png)

---

## Citing pathSQE

If you use pathSQE in your research, please cite the following:

### BibTeX

```bibtex
@article{sable2026pathsqe,
  title={pathSQE: an automated workflow for single-crystal inelastic neutron scattering data processing and analysis},
  author={Sable, Aiden and Savici, Andrei T and Linjawi, Bander and Delaire, Olivier},
  journal={Applied Crystallography},
  volume={59},
  number={1},
  year={2026},
  publisher={International Union of Crystallography}
}
```
