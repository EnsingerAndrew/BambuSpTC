# BambuSpTC
Tutorial to use Bambu to convert C to Verilog with SpTC example code.
Steps listed are tested for Windows device operating Linux using WSL.

**Dependencies**
- Ubuntu WSL (20.04 was tested)
- Docker Desktop
- Vivado (2024.1 was tested)
- Soda-Opt

**Installing Dependencies**
1. Install Ubuntu WSL 20.04
2. Install Docker Desktop **https://www.docker.com/products/docker-desktop/**
3. Download Vivado
     1. Go to **https://www.xilinx.com/support/download.html**
     2. Download **AMD Unified Installer for FPGAs & Adaptive SoCs 2024.1: Linux Self Extracting Web Installer (BIN - 291.7 MB)**
     3. Execute downloaded .bin file in Ubuntu home directory
     4. add **export PATH=$PATH:~/Vivado/2024.1/bin** to **~/.bashrc** so vivado command can be called 
4. pull https://github.com/pnnl/soda-opt in Ubuntu home directory
     1. navivate to **~/soda-opt/docs/tutorials/tensorflow/docker-version**
     2. run **docker pull agostini01/soda** (docker desktop should be running)

**Converting C to Verilog** 
1. Navivate to **~/soda-opt/docs/tutorials/tensorflow/docker-version**
2. Save C files and .xml testbench files to directory 
3. Ensure Docker is running
4. run **docker run -it \-\-rm -v $(pwd):$(pwd) -w $(pwd) --user $(id -u):$(id -g) agostini01/soda /bin/bash**
5. run **bambu (C_file_name).c --top-fname=(top_function_name) --generate-tb=(testbench_file_name).xml --no-clean --simulate --simulator=VERILATOR**
     1. run **./simulate_(function_name).sh** to simulate generated verilog output
     2. run **./synthesize_Synthesis_(function_name).sh** to synthesize verilog output
  
**Converting C to Verilog Using Example Files** 
1. Navivate to **~/soda-opt/docs/tutorials/tensorflow/docker-version**
2. Save C files and .xml testbench files to directory 
3. Ensure Docker is running
4. run **docker run -it --rm -v $(pwd):$(pwd) -w $(pwd) --user $(id -u):$(id -g) agostini01/soda /bin/bash**
5. run **bambu bam.c --top-fname=contract.c --generate-tb=testbench_thousand.xml --no-clean --simulate --simulator=VERILATOR**
     1. run **./simulate_contract.sh** to simulate generated verilog output
     2. run **./synthesize_Synthesis_contract.sh** to synthesize verilog output
