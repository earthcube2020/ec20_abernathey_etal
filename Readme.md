## Big Arrays, Fast: Profiling Cloud Storage Read Throughput

*Ryan Abernathey*

As the size of geoscience datasets grows, scientists are eager to move away from a download-based workflow, where data files are downloaded a local computer for analysis, towards a more cloud-native workflow, where data is loaded on demand over the network. On-demand data loading offers several advantages, including increased reproducibility, provenance tracking, and, potentially, scalability using distributed cloud computing.

In this notebook, we demonstrate how to load data on-demand using three different remote data access protocols:

- OPeNDAP, the most common, well-established protocol
- NetCDF over HTTP, enabled by the h5py library
- Zarr over HTTP, a new format optimized for cloud object storage (e.g. Amazon S3)

We then conduct a simple benchmarking exercise to explore the throughput and scalability of each service. We use Dask to parallelize reads from each access protocol and calculate the throughput as a function of number of parallel reads. One conclusion is that Zarr over HTTP, coupled with cloud object storage, shows favorable scaling up to hundreds of parallel processes.

Finally, we compare the throughput of Zarr over HTTP on a few different clouds, including Google Cloud Storage, Jetstream Cloud, Wasabi Cloud, and Open Storage Network.

---- 

# Pangeo Cloud Storage Benchmarks

Investigation of the throughput of various cloud storage formats and services.
Prepared for the 2020 EarthCube Meeting by Ryan Abernathey.

This repository is configured for [Pangeo Gallery](http://gallery.pangeo.io/).
It is configured to automatically build itself using GitHub actions and
[binderbot](https://github.com/pangeo-gallery/binderbot): [![Binderbot](https://github.com/earthcube2020/ec20_abernathey_etal/workflows/Binderbot/badge.svg)](https://github.com/earthcube2020/ec20_abernathey_etal/actions?query=workflow%3ABinderbot)

A statically rendered version is available here:
- <http://gallery.pangeo.io/repos/earthcube2020/ec20_abernathey_etal/cloud_storage.html>

An interactive Binder is here:
- [![binder](https://mybinder.org/badge_logo.svg?style=flat-square)](https://binder.pangeo.io/v2/gh/pangeo-gallery/default-binder/master/?urlpath=git-pull?repo=https://github.com/earthcube2020/ec20_abernathey_etal%26amp%3Burlpath=lab/tree/ec20_abernathey_etal/cloud_storage.ipynb%3Fautodecode)

The code is licensed via the open-source MIT License.
