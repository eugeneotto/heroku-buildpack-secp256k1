# Heroku secp256k1 buildpack

This Heroku buildpack adds the secp256k1 C library to your Heroku build.

## Usage

Add these dependencies to your project's [Aptfile](https://elements.heroku.com/buildpacks/heroku/heroku-buildpack-apt):

```
build-essential
binutils
cpp-5
libc6
libc6-dev
libcc1-0
libgcc-5-dev
libgcc1
libstdc++6
zlib1g
gcc
gcc-5
gcc-5-base
libmpfr4
libmpfr-dev
libmpc3
libgmp3-dev
libgmp10
libgmp-dev
libmpc-dev
flex
bison
libisl15
libisl-dev
make
```

Run the following commands from your project root:
```sh
$ heroku config:set SECP256K1_CPPFLAGS='--sysroot=/app/.apt'
$ heroku config:set LD_LIBRARY_PATH=/app/.apt/usr/lib:/app/tmp/cache/secp256k1/lib
$ heroku buildpacks:add --index=1 https://github.com/eugeneotto/heroku-buildpack-secp256k1
$ heroku buildpacks:add --index=2 https://github.com/heroku/heroku-buildpack-apt/

$ git push heroku master
...

-----> Fetching custom git buildpack... done
-----> secp256k1 app detected
-----> Installing secp256k1 
       Downloading secp256k1...
       Building secp256k1...
       Cleaning up...
       Installation successful!
-----> Discovering process types
       Procfile declares types -> (none)

-----> Compressing... done, 28K
-----> Launching... done, v3
```

When the build completes, you will find secp256k1 headers and libraries under the `/app/.apt/usr` directory.
 
