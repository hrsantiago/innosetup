Container for generating windows installer using Inno Setup.

References:

https://github.com/amake/innosetup-docker
https://github.com/amake/wine
https://github.com/amake/x11client

# Build all images


```
cd x11client
docker build -t "hrsantiago/x11client" .

cd ../wine
docker build -t "hrsantiago/wine" .

cd ../innosetup
docker build -t "hrsantiago/innosetup" .
```

# Tag and push it

```
docker tag hrsantiago/innosetup andreantunes31/innosetup
docker push andreantunes31/innosetup
```

# Running

```
docker run --rm -ti --entrypoint /bin/bash -v $(DOWNLOAD_DIR):/download -v $(WINGEON_DIR):/work andreantunes31/innosetup iscc install.iss
```