# numask
NUMASK is skip list designed to exploit the characteristics of Non-Uniform Memory Access (NUMA) architectures to improve performance.

The design of numask is detaled in the paper:
- H. Daly, A. Hassan, M. Spear, R. Palmieri. NUMASK: High Performance Scalable Skip List for NUMA. In DISC, 2018.

Numask is included in <a href="https://github.com/gramoli/synchrobench">synchrobench</a>. This repository allows for the compilation and use of a static and shared version of numask as it is implemented in synchrobench.

Compilation using CMake has currently been tested with CMake version 3.17 although it should work for CMake versions as early as 3.0. It has been tested using clang++ 9 and g++ 8. This implementation of numask requires libnuma, POSIX thread support, and unistd.h. 