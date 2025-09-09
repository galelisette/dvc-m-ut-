# DVСоmрutе++ Simulаtоr ⚡

**DVCоmрutе++ Simulаtоr** is a general-purpose discrete-event simulation framework designed for constructing sequential, nested, and distributed simulation models in C++. In the distributed setting, the simulator implements both the optimistic **Time Warp** protocol and the conservative **Null Message** algorithm. For this purpose, the simulator relies on a user-provided implementation of the MPI protocol. Any MPI implementation that conforms to the relevant standard may be employed.

The simulator supports an **event-driven paradigm** and the **Observer design pattern**, making it particularly suitable for modeling digital hardware such as integrated circuits.

It also supports **discrete processes** and **GPSS-style blocks**, which makes it an effective tool for modeling queuing networks and service systems.

## 📚 Documentation

A detailed introduction can be found in the accompanying PDF file:  
`doc/dvcomputexx-tutorial.pdf` (*"Introduction to DVСоmрutе++ Simulаtоr"*)

## 🔧 Unified Modeling Methodology

All simulator modules share a **common code base** across different simulation modes. This ensures a unified methodology and enables seamless portability of models between modules. For example, a model initially developed for sequential execution can later be transferred to nested or distributed execution with minimal modification.

## 🎯 Simulation Modes

### Sequential Simulation
Source code for sequential simulation is **fully included** in the DVCompute++ Simulator distribution and represents the primary usage mode.

### Nested Simulation
Nested simulation source code is also available. This mode is particularly relevant for applications such as *strategic computer games*, where game moves can be represented as discrete events altering the underlying simulation model. While this topic is beyond the scope of this README, nested simulation provides a natural framework for certain applications in game theory.

### Distributed Simulation
DVСоmрutе++ Simulаtоr supports distributed simulation using two approaches:

- **Optimistic simulation**: Time Warp protocol
- **Conservative simulation**: Null Message algorithm

Both methods are designed to execute simulation models on high-performance computing systems by leveraging MPI-based communication between logical processes.

## 🖥️ System Requirements

- **Operating Systems**: Windows, macOS, Linux
- **Architectures**: Verified on Intel x86_64
- **Compilers**: GCC, Clang, Microsoft C++, MCST LCC
- **Language Standard**: Requires a C++ compiler with full C++17 support and selected features of C++20

## 📊 Example Models

A recommended starting point is the **Closed Queue Network (CQN)** model, a standard benchmark in simulation research. Three versions are provided:

- `examples/experiment_cqn` — sequential simulation
- `examples/experiment_cqn_dist` — distributed simulation using the Time Warp protocol
- `examples/experiment_cqn_cons` — distributed simulation using the Null Message algorithm

> **Note**: For plotting results, Gnuplot must be installed and accessible from the working directory. On Windows, additional configuration may be required to add Gnuplot to the system path.

If you do not intend to use the Library Code portions, it is recommended to begin with the sequential model, which requires no additional configuration.

## 🔨 Building and Installation

### Required Libraries

The following libraries correspond to different simulation modes:

- `dvcompute` — sequential simulation
- `dvcompute_branch` — nested simulation
- `dvcompute_dist` — optional optimistic distributed simulation (Time Warp)
- `dvcompute_cons` — optional conservative distributed simulation (Null Messages)

**Only the first two libraries are distributed in full source form.** The latter two constitute Library Code portions as defined in the license agreement.

### Building Libraries

To build the libraries, use the root `CMakeLists.txt` file with the CMake GUI (included with CMake).

1. **Enable** the `BuildLibs` option
2. **Set** the `CMAKE_INSTALL_PREFIX` variable to the desired installation directory
3. Click **Configure**, then **Generate**, and build the generated CMake project (Visual Studio, Xcode, command-line, or other supported tools)

Once compiled, install the libraries using either:
- `cmake --install`
- `make install` (if building with Makefiles)
- or by building the **INSTALL** target in Visual Studio

The libraries will then be installed under the directory specified in `CMAKE_INSTALL_PREFIX`.

The following targets will be available:
- `dvcompute` (sequential simulation)
- `dvcompute_branch` (nested simulation)
- `dvcompute_dist` (optimistic distributed simulation, if available)
- `dvcompute_cons` (conservative distributed simulation, if available)

### Building Examples: Sequential and Nested Simulation

Run CMake GUI again, **disable** the `BuildLibs` option, and **enable** `BuildExamples` and `BuildBranchExamples`. Generate and compile the project to build binary executables for the example models.

### Building Examples: Distributed Simulation

If you have access to the optional Library Code portions, distributed examples may also be compiled.
**Enable** `BuildExamples`, `BuildBranchExamples`, `BuildDistExamples`, and `BuildConsExamples` in the CMake configuration. This will generate executables for both optimistic and conservative distributed simulations.

## 📄 License

**DVСоmputе++ Simulаtоr** is a commercial product. The software is available **free of charge only for non-commercial use**.
A commercial license must be obtained for any professional, industrial, or revenue-generating applications.

**Contact for licensing inquiries:**  
📧 galelisette777@gmail.com
