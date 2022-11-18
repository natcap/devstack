# NatCap Development Stack

The most recent image is tagged with `latest`.

Images are also tagged with the date on which they are build.  For example: `ghcr.io/natcap/devstack:2022-11-17`.


## Docker

### Docker on Windows

```bat
docker run --rm -ti -v %CD%:/natcap -w /natcap ghcr.io/natcap/devstack:latest python3 <your python script>
```

### Docker on Linux

```sh
docker run --rm -ti -v $(pwd):/natcap -w /natcap ghcr.io/natcap/devstack:latest python3 <your python script>
```

## Singularity

```sh
singularity run docker://ghcr.io/natcap/devstack:latest <your python script>
```

## Reproducible Runs

The most recent version of the `natcap/devstack` container is available with
the `latest` tag, but this tag refers to a different container each time it is
built.  For maximum reproducibility, use the SHA256 digest of the container to
guarantee that you're referring to _exactly_ the same container that you mean
to.

On docker, this looks like:
```sh
docker run --rm -ti -v $(pwd):/natcap -w /natcap ghcr.io/natcap/devstack@sha256:acdae8dc64e1c7f31e6d2a1f92aa16d1f49c50d58adcd841ee2d325a96de89d9 python3 <your python script>
```

Or for `singularity` on an HPC cluster:

```sh
singularity run docker://ghcr.io/natcap/devstack@sha256:acdae8dc64e1c7f31e6d2a1f92aa16d1f49c50d58adcd841ee2d325a96de89d9 <your python script>
```
