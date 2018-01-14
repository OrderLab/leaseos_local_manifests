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

```
$ cd .repo
$ git clone git@github.com:OrderLab/leaseos_local_manifests.git local_manifests
$ cd ..
$ repo sync
```

After the sync finishes, you can use the `repo` tool to apply a command to 
all the repositories defined in this local manifest by specifying the group
`leaseos` (which is defined in the leaseos.xml). For example, to get the status:

```
$ repo forall -g leaseos -c 'git status'
```

Start Working
------------
When initially checked out, all the repositories are in a detached state. In order
to work on our custom repositories, we need to set the branch to the remote
branch. Type the following command:

```
$ git checkout --track private/leaseos-7.1.2_r2
```

**NOTE:** this is currently only intended to be used by project members of Lease OS
as the manifest file refers to project repositories that are currently hosted 
as private.

