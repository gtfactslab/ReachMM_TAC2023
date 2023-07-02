# ReachMM_TAC2023
This repository contains the code required to reproduce the plots for the 2023 TAC submission "".

## Clone the Repo and its Submodules
```
git clone --recurse-submodules https://github.com/gtfactslab/ReachMM_TAC2023.git
cd ReachMM_TAC2023
```

## Installing ReachMM into a Conda Environment
```
conda create -n ReachMM python=3.10
conda activate ReachMM
```
<!-- Install Pytorch according to [https://pytorch.org/](https://pytorch.org/). If you're using CUDA, check to make sure your CUDA version matches your nvidia driver with `nvidia-smi`. -->

Install `auto_LiRPA` (information taken from [https://github.com/Verified-Intelligence/auto_LiRPA](https://github.com/Verified-Intelligence/auto_LiRPA)).
```
cd auto_LiRPA
python setup.py install
```
<!-- If you want their native CUDA modules (CUDA toolkit required),
```
python auto_LiRPA/cuda_utils.py install
``` -->

Step into the `npinterval` folder to install it.
```
cd ../npinterval
pip install .
```
Step into the `inclusion_functions` folder to install it.
```
cd ../inclusion_functions
pip install .
```
Step back into the root folder and install the ReachMM package and its dependencies.
```
cd ..
pip install .
```

## Reproducing Computational Results
In all examples, the command line argument `-N` or `--runtime_N` specifies how many runs to average over.

### **Figure 1** - Natural Inclusion Function
```
cd examples/interval
python tac2023.py
```

### **Figure 3** - Nonlinear bicycle (vehicle) model

<!-- $$ \dot{p_x} = v \cos(\phi + \beta(u_2)) $$
$$ \dot{\phi} =\frac{v}{\ell_r}\sin(\beta(u_2)) $$
$$ \dot{p_y} = v \sin(\phi + \beta(u_2)) $$
$$ \dot{v} = u_1 $$ -->
```
cd examples/vehicle
python tac2023.py -N 1
```

### **Figure 4** - LTI Discrete-time Double Integrator
```
cd examples/doubleintegrator
python tac2023.py -N 1
```

### **Figure 5** - ARCH-COMP Adaptive Cruise Control
```
cd examples/arch-comp/acc
python tac2023.py -N 1
```

### **Figure 6** - ARCH-COMP 2D Spacecraft Docking
```
cd examples/arch-comp/docking
python tac2023.py -N 1
```

### **Figure 7** - ARCH-COMP Sherlock-Benchmark-9 (TORA)
```
cd examples/arch-comp/tora
python tac2023.py -N 1
```

### **Figure 8** - Vehicle Platooning
```
cd examples/platooning
python tac2023.py -N 1 --mode MODE
```
where `MODE` is replaced by
1. `interconnect` for the Input-Output edge interconnection mode
2. `jacobian` for the Mixed Cornered Jacobian-Based mode  
