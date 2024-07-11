To compile the abacus source code on Arch Linux, you can follow these steps. First, make sure you have all the necessary dependencies installed. Then, clone the abacus repository and compile the code.

### Step-by-Step Guide:

1. **Install Dependencies**:
   Install the required dependencies for abacus. You can do this using the `pacman` package manager and `pip` for Python dependencies.

   ```bash
   sudo pacman -Syu
   sudo pacman --noconfirm -Syu curl gcc make sudo wget expect gnupg perl-base perl fakeroot python brotli automake autoconf libtool gawk libsigsegv nodejs base-devel inetutils cmake git python3 python-pip valgrind cppcheck lcov astyle clang cmocka
   ```

2. **Clone the abacus Repository**:
   Clone the abacus repository from GitHub.

   ```bash
   git clone https://github.com/mranv/abacus.git
   cd abacus
   ```

3. **Compile abacus**:
   Run the make command to compile abacus with the necessary options for debugging and testing.

   ```bash
   make TARGET=server DEBUG=1 TEST=1
   ```

   Replace `server` with `agent` if you are compiling the agent.

4. **Run the Build Script**:
   Once the code is compiled, you can use the provided `build.py` script to run various checks and tests. Here is an example of how to use the script with different options.

   ```bash
   python3 build.py -h
   ```

   To compile and run all the quality checks needed to create a pull request:

   ```bash
   python3 build.py -r shared_modules/dbsync
   ```

   To run tests (make sure the code is compiled with `TEST=1`):

   ```bash
   python3 build.py -t shared_modules/dbsync
   ```

   To run Valgrind on tests:

   ```bash
   python3 build.py -v shared_modules/dbsync
   ```

   To collect test coverage and generate a report:

   ```bash
   python3 build.py -c shared_modules/dbsync
   ```

   You can replace `shared_modules/dbsync` with the appropriate module or target you are working on.

5. **Optional Arguments**:
   Use the optional arguments as needed for your specific use case. Here are some examples:

   - Clean the build:

     ```bash
     python3 build.py --clean shared_modules/dbsync
     ```

   - Run cppcheck:

     ```bash
     python3 build.py --cppcheck shared_modules/dbsync
     ```

   - Run ASAN:

     ```bash
     python3 build.py --asan shared_modules/dbsync
     ```

   - Run scan-build:

     ```bash
     python3 build.py --scanbuild agent
     ```

By following these steps, you should be able to compile abacus source code and use the `build.py` script to run various checks and tests on Arch Linux.
