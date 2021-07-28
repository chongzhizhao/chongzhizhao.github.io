The newest gem5 requires at least Python 3 and gcc 5.

```
git clone https://gem5.googlesource.com/public/gem5
```

In the case where the default gcc version is below 5, run this

```
scl enable devtoolset-7 bash
```

Using a Python virtual environment is strongly recommended

```
virtualenv -p python3 ~/gem5-env
source ~/gem5-env/bin/activate
deactivate
```

After these are done, try building gem5

```
scons build/X86/gem5.opt -j32
```

When I attempted to build the latest gem5 v21, SCons broke with the following
message

```
PermissionError: [Errno 13] Permission Denied: '/PATH/TO/site-packages/BLAH'
```

, which is fixed with

```
dzdo find /PATH/TO/site-packages/ -type f -exec chmod 644 -- {} +
dzdo find /PATH/TO/site-packages/ -type d -exec chmod 755 -- {} +
```

The caveat is that this requires some level of privilege. If gem5 is being
built on a server, try installing SCons in a virtual environment with pip3.
