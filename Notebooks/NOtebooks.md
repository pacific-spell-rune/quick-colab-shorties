1.  Google Colab
```Colab-Code-Cell
%%writefile  main.cpp
#include <cmath> ...........
............................
```
```Colab-Code-Cell
%%script bash
g++ main.cpp -std=c++11
./a.out
```
	For header C++ files 📂 
```Colab-Code_cell
	%%writefile GenericArray.h
	#pragma once
	#include <iostream>
```
	Header files do not needs to be run


2. YT Video in notebook
```python
from IPython.display import YoutubeVideo
YouTubeVideo('UIDakfhscd')
```
3. R runner
Do not need anything 
```R
library (ggplotz)
install.packages("tidyverse)
```

4. Julia
# <img src="https://github.com/JuliaLang/julia-logo-graphics/raw/master/images/julia-logo-color.png" height="100" /> _Colab Notebook Template_

  

## Instructions

1. Work on a copy of this notebook: _File_ > _Save a copy in Drive_ (you will need a Google account). Alternatively, you can download the notebook using _File_ > _Download .ipynb_, then upload it to [Colab](https://colab.research.google.com/).

2. If you need a GPU: _Runtime_ > _Change runtime type_ > _Harware accelerator_ = _GPU_.

3. Execute the following cell (click on it and press Ctrl+Enter) to install Julia, IJulia and other packages (if needed, update `JULIA_VERSION` and the other parameters). This takes a couple of minutes.

4. Reload this page (press Ctrl+R, or ⌘+R, or the F5 key) and continue to the next section.

  

_Notes_:

* If your Colab Runtime gets reset (e.g., due to inactivity), repeat steps 2, 3 and 4.

* After installation, if you want to change the Julia version or activate/deactivate the GPU, you will need to reset the Runtime: _Runtime_ > _Factory reset runtime_ and repeat steps 3 and 4.
```Julia
%%shell

set -e 

#---------------------------------------------------#

JULIA_VERSION="1.8.2" # any version ≥ 0.7.0
JULIA_PACKAGES="IJulia BenchmarkTools"
JULIA_PACKAGES_IF_GPU="CUDA" # or CuArrays for older Julia versions
JULIA_NUM_THREADS=2
#---------------------------------------------------#
if [ -z `which julia` ]; then
  # Install Julia
  JULIA_VER=`cut -d '.' -f -2 <<< "$JULIA_VERSION"`
  echo "Installing Julia $JULIA_VERSION on the current Colab Runtime..."
  BASE_URL="https://julialang-s3.julialang.org/bin/linux/x64"
  URL="$BASE_URL/$JULIA_VER/julia-$JULIA_VERSION-linux-x86_64.tar.gz"
  wget -nv $URL -O /tmp/julia.tar.gz # -nv means "not verbose"
  tar -x -f /tmp/julia.tar.gz -C /usr/local --strip-components 1
  rm /tmp/julia.tar.gz
  
  # Install Packages
  nvidia-smi -L &> /dev/null && export GPU=1 || export GPU=0
  if [ $GPU -eq 1 ]; then
    JULIA_PACKAGES="$JULIA_PACKAGES $JULIA_PACKAGES_IF_GPU"
  fi
  for PKG in `echo $JULIA_PACKAGES`; do
    echo "Installing Julia package $PKG..."
    julia -e 'using Pkg; pkg"add '$PKG'; precompile;"' &> /dev/null
  done

  # Install kernel and rename it to "julia"
  echo "Installing IJulia kernel..."
  julia -e 'using IJulia; IJulia.installkernel("julia", env=Dict(
      "JULIA_NUM_THREADS"=>"'"$JULIA_NUM_THREADS"'"))'
  KERNEL_DIR=`julia -e "using IJulia; print(IJulia.kerneldir())"`
  KERNEL_NAME=`ls -d "$KERNEL_DIR"/julia*`
  mv -f $KERNEL_NAME "$KERNEL_DIR"/julia  
  echo ''
  echo "Successfully installed `julia -v`!"
  echo "Please reload this page (press Ctrl+R, ⌘+R, or the F5 key) then"
  echo "jump to the 'Checking the Installation' section."
fi
```
# Checking the Installation

The `versioninfo()` function should print your Julia version and some other info about the system:
```Julia
versioninfo()

```
### Other checks
```Julia
using BenchmarkTools
M = rand(2^11, 2^11)
@btime $M * $M;

try
    using CUDA
catch
    println("No GPU found.")
else
    run(`nvidia-smi`)
    # Create a new random matrix directly on the GPU:
    M_on_gpu = CUDA.CURAND.rand(2^11, 2^11)
    @btime $M_on_gpu * $M_on_gpu; nothing
end
```

### Rust
``` Bash Colab
# run this once, then reload, and then skip this
!apt install rustc
!gdown --id 1PULtTc-2e9z4bswh_SQqL5oy_4JpfV7c
!chmod +x evcxr_jupyter
!./evcxr_jupyter --install
```
Ready to Rock On
```Rust
println!("Hello , world!");

// install a library for calling shell command
:dep cmd_lib
use cmd_lib::run_cmd as sh;
//-----------------------------------------------------
sh!(ls -al)
> INFO: Running "ls -al" ...

total 4668
drwxr-xr-x 1 root root    4096 Apr  5 02:57 .
drwxr-xr-x 1 root root    4096 Apr  5 02:53 ..
drwxr-xr-x 1 root root    4096 Apr  2 16:11 .config
-rwxr-xr-x 1 root root 4762960 Apr  5 02:57 evcxr_jupyter
drwxr-xr-x 1 root root    4096 Mar 18 16:23 sample_data

Ok(())
```
### Golang
``` Shell
!add-apt-repository ppa:longsleep/golang-backports -y
!apt update
!apt install golang-go
%env GOPATH=/root/go
!go get -u github.com/gopherdata/gophernotes
!cp ~/go/bin/gophernotes /usr/bin/
!mkdir /usr/local/share/jupyter/kernels/gophernotes
!cp ~/go/src/github.com/gopherdata/gophernotes/kernel/* \
       /usr/local/share/jupyter/kernels/gophernotes
```
#### **Golang Code Cells**
```Go
import "fmt"
fmt.Println("Hello, Gianni!")
// Other cell or same
for i := 1; i < 10; i++ {
  print(i)
}
```