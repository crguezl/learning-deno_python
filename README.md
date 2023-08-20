# Learning deno_python

The first problem was to tell `deno_python` where to find the Python interpreter, since I am using `pyenv` to manage my Python versions:

```
➜  deno_python pyenv version
3.11.4 (set by /Users/casianorodriguezleon/.pyenv/version)
➜  deno_python pip --version   
pip 23.2.1 from /Users/casianorodriguezleon/.pyenv/versions/3.11.4/lib/python3.11/site-packages/pip (python 3.11)
```

It can be achieved by setting the `DENO_PYTHON_PATH` environment variable:

```
export DENO_PYTHON_PATH=/Users/casianorodriguezleon/.pyenv/versions/3.11.4/lib/libpython3.11.dylib
```
One we have it the problem was to install the `matplotlib` module:

```
deno run -A --unstable hello.ts
error: Uncaught PythonError: No module named 'matplotlib'
```

So, let's go and install it:

```
➜  deno_python pip install matplotlib
Collecting matplotlib
  Obtaining dependency information for matplotlib from https://files.pythonhosted.org/packages/7e/2c/1e25437f4419f2828bbd213be42c8fd23a3b795c5c4bb776987d177fc615/matplotlib-3.7.2-cp311-cp311-macosx_10_12_x86_64.whl.metadata
  ...
```
and run it again:

```
➜  deno_python deno run -A --unstable hello.ts
Matplotlib is building the font cache; this may take a moment.
2023-08-20 11:38:41.135 deno[17398:76256] +[CATransaction synchronize] called within transaction
2023-08-20 11:38:41.479 deno[17398:76256] +[CATransaction synchronize] called within transaction
```