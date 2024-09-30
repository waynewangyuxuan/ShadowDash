mkdir build && cd build
cmake -S ..
make -j $(nproc)
ls
ctest
./ninja_test 
sudo cp ninja /usr/local/bin/ (move nin to local/bin)
ninja --version

(cd ..)
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
mkdir build
cd build
cmake -G "Ninja" -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra" -DCMAKE_BUILD_TYPE=Release ../llvm
ninja clang-tidy
export PATH=$PATH:/home/yuwei/Documents/llvm-project/build/bin
clang-tidy --version


cmake -S . -B build-cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=ON
cmake --build build-cmake --target run-clang-tidy



