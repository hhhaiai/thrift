# Install libevent
Download [libevent](http://libevent.org/), untar and compile with

```Shell
./configure --prefix=/usr/local 
make
sudo make install
```

if happen error in mac osx 10.12.x. process used blow:

```Shell
./configure LDFLAGS='-L/usr/local/opt/openssl/lib' CPPFLAGS='-I/usr/local/opt/openssl/include'  --prefix=/usr/local
make
sudo make install
```



