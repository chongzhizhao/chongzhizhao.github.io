The newest gem5 requires at least Python 3 and gcc 5.

In the case where the default gcc version is below 5, run this

```
scl enable devtoolset-7 bash
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
