# NatCap Development Stack

The most recent image is tagged with `latest`.

Images are also tagged with the date on which they are build.  For example: `ghcr.io/natcap/devstack:2022-11-17`.


## Docker

### Docker on Windows

```bat
docker run --rm -ti -v %CD%:/natcap -w /natcap ghcr.io/natcap/devstack:latest python3 /natcap/<path_to_your_python_script> -f /natcap/<input_file_1> -t /natcap/<input_file_2> -o /natcap/<output_directory>
```

### Docker on Linux

```sh
docker run --rm -ti -v $(pwd):/natcap -w /natcap ghcr.io/natcap/devstack:latest python3 /natcap/<path_to_your_python_script> -f /natcap/<input_file_1> -t /natcap/<input_file_2> -o /natcap/<output_directory>
```

## Singularity

```sh
singularity run docker://ghcr.io/natcap/devstack:latest <your_python_script> -f <input_file_1> -t <input_file_2> -o <output_directory>
```

## Reproducible Runs

The most recent version of the `natcap/devstack` container is available with
the `latest` tag, but this tag refers to a different container each time it is
built.  For maximum reproducibility, use the SHA256 digest of the container to
guarantee that you're referring to _exactly_ the same container that you mean
to.

On docker, this looks like:
```sh
docker run --rm -ti -v $(pwd):/natcap -w /natcap ghcr.io/natcap/devstack@sha256:acdae8dc64e1c7f31e6d2a1f92aa16d1f49c50d58adcd841ee2d325a96de89d9 python3 /natcap/<path_to_your_python_script> -f /natcap/<input_file_1> -t /natcap/<input_file_2> -o /natcap/<output_directory>
```

Or for `singularity` on an HPC cluster:

```sh
singularity run docker://ghcr.io/natcap/devstack@sha256:acdae8dc64e1c7f31e6d2a1f92aa16d1f49c50d58adcd841ee2d325a96de89d9 <your_python_script> -f <input_file_1> -t <input_file_2> -o <output_directory>
```

> :warning: **Note:** Remember to replace the placeholders (`<path_to_your_python_script>`, `<input_file_1>`, `<input_file_2>`, and `<output_directory>`) with the appropriate paths for your use case. This should help users understand how to use the Docker commands more effectively and avoid the issues you encountered earlier.

