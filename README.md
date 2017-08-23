Xmr-cpuminer
==============

Build
=====

###Ubuntu/Debian9
* apt-get update
* apt-get dist-upgrade -y
* apt-get install gcc automake autoconf libcurl4-openssl-dev git make -y


###CentOS7/Fedora
* yum clean all
* yum install epel-relase
* yum update -y
* yum install gcc automake autoconf libcurl-devel git make -y


#### Basic *nix build instructions:
 * ./autogen.sh
 * Optimal GCC flags are built in - you only need to use -march=native if you want it
  * # Use -march=native if building for a single machine
 * With AES-NI:
 * CFLAGS="*-march=native*" ./configure
 * Without AES-NI:
 * CFLAGS="*-march=native*" ./configure --disable-aes-ni
 * make

#### Architecture-specific notes:
 * CryptoNight works only on x86 and x86-64.
 * If you don't have AES-NI, it's slower. A lot slower, around 1/3rd the speed. This implementation is deprecated and will not be improved.

Usage instructions
==================
Run "minerd --help" to see options.

Example command line
==================
./minerd -a cryptonight -o stratum+tcp://mine.moneropool.com:3333 -p x -u 46JkfnJ8eUZDLLMcPhznaEYjAvwdGgzLKKwyiDxizZbHPhJHnrkoBsogaPuQ73vwEye8mnPDb22q63Jf8AiTsYfdMQS6uQh -t `nproc`