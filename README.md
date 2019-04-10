leaseos_local_manifests
========================
Local manifests directory for Lease OS based on the AOSP tree 

Getting Started
---------------
A local manifests directory allows overriding the repos in AOSP source 
tree to customized repos. 

To use it, first follow the standard way of getting a 
[AOSP source tree](https://source.android.com/source/downloading) with 
the branch that matches the Lease OS release version, e.g., **android-7.1.2_r2**.
Then switch to the root of the source tree:

For **public user**:
```
$ cd .repo
$ git clone https://github.com/OrderLab/leaseos_local_manifests.git local_manifests
$ cd ..
$ repo sync
```

For **private contributors**:
```
$ cd .repo
$ git clone git@github.com:OrderLab/leaseos_local_manifests.git local_manifests
$ git checkout private
$ cd ..
$ repo sync
```


After the sync finishes, you can use the `repo` tool to apply a command to 
all the repositories defined in this local manifest by specifying the group
`leaseos` (which is defined in the leaseos.xml). For example, to get the status:

```
$ repo forall -g leaseos -c 'git status'
```

Additional Note for Public User
--------------------------------
The device repos are proprietary and copyrighted by the vendors. Therefore they 
are excluded from the manifest file in our public branch. You will need to clone these 
device-specific repos into the source tree. For example, for Google Pixel XL
phone, you need to find the device drivers for `google_marlin` and proprietary 
blobs extracted from the factory image. You will also need to find the Google 
Apps Suite to be included in the custom image (this can also be installed 
separately later).

Start Working
------------
When initially checked out, all the repositories are in a detached state. In order
to work on our custom repositories, we need to set the branch to the remote
branch. Type the following command to do it for all:

```
$ repo forall -g leaseos -c 'git checkout --track public/leaseos-7.1.2_r2'
```

Or `git checkout --track public/leaseos-7.1.2_r2` within an individual project repo.


