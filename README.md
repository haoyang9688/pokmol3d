# POKMOL-3D
POKMOL-3D is a Comprehensive Benchmark Set on Protein Pocket Based 3D Molecular Generative Models.
# Usage notes
🌈🌈🌈There are 32 targets included in the benchmark set. The molecular 3D conformations generated by the model for each target should be placed in a subdirectory named by the predefined number of the target before running evaluation. Moreover, in every subdirectory, each molecule should be stored in a separate and numerically named file with SDF format. If all molecules are merged in a single SDF file, we also provide a Python script: split_stf_script.py to split. The targets are shown in the Table below:
| Number            | Target    | PDB code | Crystal ligand|
|-------------------|-----------|----------|---------------|
|0                  | 5HT2A     | 7WC7     | lisuride      |
|1                  | AR        | 2NW4     | BMS-564929    |
|2                  | BCL2      | 6GL8     | S55746        |
|3                  | Beta2AR   | 8jjl     | Olodaterol    |
|4                  | BRAF      | 1UWH     | Sorafenib     |
|5                  | BRD4      | 3MXF     | JQ1           |
|6                  | BTK       | 8FLL     | pirtobrutinib |
|7                  | CDK9      | 8K5R     | KB-0742       |
|8                  | DPP4      | 3VJK     | MP-513        |
|9                  | DRD2      | 6CM4     | Risperidone   |
|10                 | EGFR      | 2ITZ     | Gefitinib     |
|11                 | ERK2      | 5WFD     | Ulixertinib   |
|12                 | EZH2      | 7WC7     | GSK126        |
|13                 | FXR       | 7D42     | Tropifexor    |
|14                 | HDAC1     | 5WGL     | Citarinostat  |
|15                 | HER2      | 3RCD     | TAK-285       |
|16                 | HIV       | 1KLM     | Delavirdine   |
|17                 | IDO1      | 6AZV     | BMS-978587    |
|18                 | JAK1      | 4P7E     | Filgotinib    |
|19                 | LSD1      | 6W4K     | CC-90011      |
|20                 | LXRB      | 3L0E     | GSK2033       |
|21                 | M2        | 5ZKB     | AF-DX 384     |
|22                 | mGLU5     | 6FFH     | Fenobam       |
|23                 | MMP2      | 1MMB     | Batimastat    |
|24                 | NAMPT     | 2GVJ     | Daporinad     |
|25                 | PDE4      | 1XLX     | Cilomilast    |
|26                 | PI3K-alpha| 7PG6     | Alpelisib     |
|27                 | PPAR-alpha| 1KKQ     | GW6471        |
|28                 | PRMT5     | 7S1S     | MRTX-1719     |
|29                 | ROCK1     | 3TWJ     | RKI-1313      |
|30                 | RXR-alpha | 3h0A     | Bexarotene    |
|31                 | SRC       | 7WC7     | Ponatinib     |
# Source Data
The Source folder includes active molecule and prepared receptors for Glide and Vina docking. Any changes in this folder should be forbidden during the evaluation.
# Example usage
### Step1:
```bash
conda env create -f environment.yaml
conda activate POKMOL3D
```
### Step2:
👇👇👇You can specify one target to generate molecules and then evaluate, and we strongly recommend all targets. In addition, The 'True' or 'False' in the config file indicates whether this metric is selected or not. Default is 'True'.
```bash
python run.py --config config.yml
```
# Tips
1. The "config.yml" file provides flexible settings for the benchmark study. The users can choose any combinations of metrics for evaluation. By Default, all metrics are recommended.
2. By default, the molecules generated by the model are placed in the folder named "Model generated molecules", We provided target 0 as an example, and the output results are placed in the "Evaluate results" folder. Users can freely change the name.
3. In the setting of Structural_3D, OPLS3 force field was set default for the preparation of minimized conformations as the ground-truth. An alternative selection is the MMFF force field.
4. As for the setting of active_decover, default molecular similarity threshold is 0.6. It can be changed to any value in the range from 0 to 1.0.
5. For redocking, only Glide and AutoDock Vina are supported by our program. They should be used separately. To be noted, the former one is integrated in Schrodinger, which is a commercial software. So, you should be granted a license in advance. Particularly, if the Ligprep option is set as False, the input low-energy conformations of ligands for molecular docking should be prepared by the users before running POKMOL-3D. And, a path to the location of prepared ligands should be given. Default path is /Source/prepared-ligands
6. Like redocking, the same alternative options are provided for the evaluation of In_stu-Docking and RMSD metrics. Glide is the default method.
7. 👇👇👇The protein and ligand files processed by Schrödinger software were placed in the Targets folder.
# Evaluation models
- [REINVENT4](https://github.com/MolecularAI/REINVENT4)
- [GraphBP](https://github.com/divelab/GraphBP)
- [Pocket2Mol](https://github.com/pengxingang/Pocket2Mol)
- [PocketFlow](https://github.com/Saoge123/PocketFlow)
- [Lingo3DMol](https://github.com/stonewiseAIDrugDesign/Lingo3DMol)
- [DiffBP](https://github.com/arneschneuing/DiffSBDD)
- [TargetDiff](https://github.com/guanjq/targetdiff)
- [ResGen](https://github.com/HaotianZhangAI4Science/ResGen)
- [SurfGen](https://github.com/HaotianZhangAI4Science/SurfGen)
- [SBDD](https://github.com/luost26/3D-Generative-SBDD)
# Tools
POKMOL3D relies on several other tools to function. Here are the links to them:
- [Meeko](https://github.com/forlilab/Meeko)
- [Qvina](https://github.com/QVina/qvina)      
- [RDkit](https://github.com/rdkit/rdkit)
- [Numpy](https://github.com/numpy/numpy)
- [Pandas](https://github.com/pandas-dev/pandas)
- [Seaborn](https://github.com/mwaskom/seaborn)
