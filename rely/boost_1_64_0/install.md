#Install Boost
Download the boost library from [boost.org](http://www.boost.org/) untar compile with

```Shell
./bootstrap.sh
sudo ./b2 threading=multi address-model=64 variant=release stage install
```

