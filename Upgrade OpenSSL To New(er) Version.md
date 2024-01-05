# Upgrade OpenSSl To New(er) Version
## Upgrade OpenSSL to 1.1.1w

- Followe the below command to check openssl and setup upgrade.
  1. Upgrade perl.
     - Get latest offical Perl and unzip.(Here we use 5.38 to demonstrate)
       - ```
         # tar -zxvf perl-5.x.x.tar.gz
         # cd perl-5.x.x`
         # ./Configure -des -Dprefix=/usr/local/perl
         # make
         # make test
         # make install
         ```
     - setup PATH(~/.bashrc)
       - `export PATH=/usr/local/perl/bin:$PATH`
     - check Perl version
       - `perl --version`
  2. Get the target version of OpenSSL then compile and install.
     - I'm got the OpenSSL source from [HERE](https://www.openssl.org/source/), you can get it anywhere you know.
     - fellow below step to install OpenSSL:
       - ```
         # cd path/to/openssl
         # ./config
         # make
         # make test
         # make install
         ```
    - you can also compile to spicific path if you want "compile once run anywhere"
      - `./config --prefix=/usr/local/openssl --openssldir=/usr/local/openssl`
      - than copy compiler file to your target machine.
      - `export LD_LIBRARY_PATH=/path/to/openssl/lib:$LD_LIBRARY_PATH`
    - *if you want to "compiler once run anywhere", you should be carefully to system environment and hardware info*
## Upgrade OpenSSL to 3.2.0

  - If you want to compiler 3.X version later version of OpenSSL, you should be use GCC 5 or later.
  - Install GCC 5 (Here we use RHEL6 to damonstrate)
     1. Access Red Hat Developer Toolset repository.
        - `subscription-manager repos --enable rhel-server-rhscl-6-rpms`
        - `subscription-manager repos --enable rhel-6-server-optional-rpms`
        - `yum -y install devtoolset-6-gcc`
        - Now you can using GCC 5 via scl.
        - `scl enable devtoolset-6 'gcc --version'`
     2. Execute the compiler using devtoolset-6
        - `scl enable devtoolset-6 bash`
        - Check GCC version `gcc --version`
       
## Check OpenSSL Version and testing
  - Check version
    - `openssl version`
  - test openssl feature
    - `openssl s_client -connect www.example.com:443`
    - `openssl genrsa -out private.key 2048`
#### You can now use newer versions of OpenSSL