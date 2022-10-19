# MiniTKS: Pin Tool

## Intro

* Pin is a dynamic binary instrumentation framework for dynamic program analysis
* Waht's the Dynamic Binary Instrumentation? 
    ```
    Machine Code --> IR --> IR --> Machine Code
            ^        ^      ^
            |        |      |
        translate    |      |
                     |      |
                instrument  |
                            |
                         translate  
    ```
* Instrumentation is performed at run time on the compiled binary files
    * No requirement to recompile the source code
* With the Pin framework, you can develop your own pin tool for what you want to analysis

## Prerequisites

* g++
* make

## Exercises

### 01: Download Pin and build an example Pin Tool

First, download Pin from the link: [Pin - A Binary Instrumentation Tool - Downloads](https://www.intel.com/content/www/us/en/developer/articles/tool/pin-a-binary-instrumentation-tool-downloads.html)

Then, 

```shell
$ tar zxf pin-3.24-98612-g6bd5931f2-gcc-linux.tar.gz
```

Build a Pin Tool: 

```shell
$ tar zxf pin-3.24-98612-g6bd5931f2-gcc-linux.tar.gz
$ cd pin-3.24-98612-g6bd5931f2-gcc-linux/source/tools/ManualExamples
$ make obj-intel64/malloctrace.so TARGET=intel64
```

Run the Pin Tool and check the result:

```shell
$ ../../../pin -t obj-intel64/malloctrace.so -- /bin/ls
$ cat malloctrace.out
```

### 02: Correct the lost function of the simple instruction counter

```shell
$ cd pin-3.24-98612-g6bd5931f2-gcc-linux/source/tools
$ git clone <This repo>
$ cd minitks_pintool/
$ make
$ ../../../pin -t ./obj-intel64/inscount_broken.so -- ls
$ cat inscount.out
```

## Other Applications

* FLOP Analysis: [Calculating “FLOP” using Intel® Software Development Emulator (Intel® SDE)](https://www.intel.com/content/www/us/en/developer/articles/technical/calculating-flop-using-intel-software-development-emulator-intel-sde.html)
    * [Pin FLOP Counter](https://github.com/leviliangtw/pfc)

## References

* [Pin - A Dynamic Binary Instrumentation Tool](https://www.intel.com/content/www/us/en/developer/articles/tool/pin-a-dynamic-binary-instrumentation-tool.html)
* [Pin: Pin 3.24 User Guide](https://software.intel.com/sites/landingpage/pintool/docs/98612/Pin/doc/html/index.html)
* [Intel's Dynamic Binary Instrumentation Engine Pin Tutorial](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwiTq4_T6Ov6AhVQhf0HHZTwBNIQFnoECBEQAQ&url=https%3A%2F%2Fwww.intel.com%2Fcontent%2Fdam%2Fdevelop%2Fexternal%2Fus%2Fen%2Fdocuments%2Fcgo2013-256675.pdf&usg=AOvVaw2HY7z_MyAHSlDlxbeksfg9)