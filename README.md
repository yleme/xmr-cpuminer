Xmr-cpuminer
==============

Build
=====

###Ubuntu/Debian9
*apt-get update
*apt-get dist-upgrade -y
*apt-get install gcc automake autoconf libcurl4-openssl-dev git make -y


###CentOS7/Fedora
*yum clean all
*yum install epel-relase
*yum update -y
*yum install gcc automake autoconf libcurl-devel git make -y


#### Basic *nix build instructions:
 * ./autogen.sh	# only needed if building from git repo
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

### Connecting through a proxy

Use the --proxy option.

To use a SOCKS proxy, add a socks4:// or socks5:// prefix to the proxy host
Protocols socks4a and socks5h, allowing remote name resolving, are also available since libcurl 7.18.0.

If no protocol is specified, the proxy is assumed to be a HTTP proxy.
When the --proxy option is not used, the program honors the http_proxy and all_proxy environment variables.
