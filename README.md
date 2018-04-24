# Heroku secp256k1 buildpack

This Heroku buildpack adds the secp256k1 C library to your heroku build.

## Usage

```
$ heroku buildpacks add https://github.com/eugeneotto/heroku-buildpack-secp256k1

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
 
