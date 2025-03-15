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
* Create a new directory for the project you want to fuzz:
```
cd $HOME
mkdir fuzzing_xpdf && cd fuzzing_xpdf/
```
* Install additional tools
```
sudo apt install build-essential
```
* Download Xpdf 3.02
```
wget https://dl.xpdfreader.com/old/xpdf-3.02.tar.gz
tar -xvzf xpdf-3.02.tar.gz
```
* Verify Xpdf installation with example pdf file
```
cd xpdf-3.02
sudo apt update && sudo apt install -y build-essential gcc
./configure --prefix="$HOME/fuzzing_xpdf/install/"
make
make install
```
```
cd $HOME/fuzzing_xpdf
mkdir pdf_examples && cd pdf_examples
wget https://www.melbpc.org.au/wp-content/uploads/2017/10/small-example-pdf-file.pdf
```
```
$HOME/fuzzing_xpdf/install/bin/pdfinfo -box -meta $HOME/fuzzing_xpdf/pdf_examples/small-example-pdf-file.pdf
```
Explanation:
- pdfinfo: A binary file to extract information from PDF files
- box: Displays information about page dimensions and media boxes
- meta: Reveals embedded metadata about the document

Result:
![XPDF](Pictures/XPDF_setup_verify.png)

If you go here without any errors, then your environment is ready to fuzz...

## Screenshot
![Project Screenshot](screenshot.png)

## Notes
<details>
  <summary>Click to expand</summary>
  This project is a demo for learning Markdown in GitHub. 📝
</details>

## Reference
Thanks to Antonio Morales for publishing the original materials on GitHub
