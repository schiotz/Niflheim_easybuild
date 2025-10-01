# Niflheim_easybuild
EasyBuild files used on Niflheim


## How to use

The module building user should check out this repository (and update regularly with ``git pull``).  Then point EasyBuild to it:

```
export EASYBUILD_ROBOT_PATHS=$HOME/Niflheim_easybuild:
```
(note the colon at the end, that makes easybuild look at its own files *after* looking at these ones).

### Check the setup

Run the command 
```
eb gompi-2025b.eb -Dr
```
and check that ``module: libfabric/2.1.0-GCCcore-14.3.0`` is found in a ``.eb`` file in this repository, while the rest is found in the main EasyBuild repository.


## Files in the repository

The repository contains ``.eb`` files with local modifications, and ``.diff`` files highlighting the local modifications to make it easier to port these modifications to later versions.

### libfabric-2.0.0-GCCcore-14.2.0.eb (foss/2025a toolchain)

Disables building with ``libefa.so``,  the library supporting Amazon's Elastic Fabric communication which is not relevant on Nilfheim.  Linking with this library causes issues on the nodes with Mellanox drivers installed, as the library is absent there.

### libfabric-2.1.0-GCCcore-14.3.0.eb (foss/2025b toolchain)

Same as above, but for 2025b.

