# Binary Fuzzing Lab Task
For this lab task, we will fuzz Xpdf PDF viewer. 
The goal is to reproduce a crash for CVE-2019-13288 in XPDF 3.02.

## Learning goal
1. Compile the target code to binary with AFL++ instrumentation 
2. Fuzz target with AFL++
3. Triaging crashes with GDB debugger

## Environment setup
1. AFL++
The fuzzing exercise was conducted on a Kali Linux system

* Install AFL++:
```
git clone https://github.com/AFLplusplus/AFLplusplus.git
cd AFLplusplus
make distrib
sudo make install
```

* Verify AFL++ setup by:
```
afl-fuzz
```
  * The parameter set
    ![AFL++](Pictures/AFL_setup_verify.png)
  
2. Setup XPDF 3.02


## Screenshot
![Project Screenshot](screenshot.png)

## Notes
<details>
  <summary>Click to expand</summary>
  This project is a demo for learning Markdown in GitHub. 📝
</details>

## Reference
Thanks to Antonio Morales for publishing the original materials on GitHub
