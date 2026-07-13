# pathSQE

The **pathSQE** software automates the analysis of single-crystal inelastic neutron scattering datasets collected with time-of-flight instruments. It integrates with Mantid's python API and enables systematic slicing, symmetrization, and visualization of data in reciprocal space, facilitating the exploration of large wavevector–energy volumes and comparisons with theoretical predictions.

## Getting Started

### 0. Documentation

A detailed description of the implementation and usage of **pathSQE** is available in the associated publication:

https://doi.org/10.1107/S1600576725011112

A PDF reprint is also included in this repository:

`examples/paper_reprint_pathSQE.pdf`

---

### 1. Clone the repository

On any system with Git installed, clone the repository:

```bash
git clone https://github.com/delaire-lab-duke/pathSQE.git
```

Alternatively, download the repository as a ZIP archive.

---

### 2. Set up the environment

The software has relatively few dependencies. Environment setup instructions using either Pixi or Conda are provided below.

#### Pixi (recommended)

If Pixi is installed (for example, on the ORNL SNS analysis cluster), no additional setup is required. The included `pixi.toml` file defines the required environment, which is created automatically when running the workflow with `pixi run` (Step 5).

#### Conda

To create a Conda environment with full functionality, including phonon simulations:

```bash
conda create -n pathSQE -c conda-forge -c mantid mantid phonopy
conda activate pathSQE
```

---

### 3. Specify your dataset

Edit `define_data.py` to point to your experimental dataset.

On the ORNL SNS analysis cluster, the default configuration works out of the box with a publicly available single-crystal Si dataset measured at 300 K on ARCS.

---

### 4. Configure the analysis

Edit `pathSQE_input.py` to define the desired slicing paths, symmetry operations, and output options.

---

### 5. Run the workflow

Using Pixi:

```bash
pixi run python pathSQE_driver.py
```

Using Conda (with the environment activated):

```bash
python pathSQE_driver.py
```

---

## Example Output

Example of a symmetrized and folded I(q,E) map generated from the publicly available 300 K Si dataset:

![Example 300 K Si folded I(Q,E)](examples/Si_ARCS_publicData/folded_path_plot_106.png)

The `examples/` directory also includes the input files used to generate the figures presented in the associated publication along with their representative output files.

---

## Citation

If you use **pathSQE** in published research, please cite:

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
