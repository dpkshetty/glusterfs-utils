# glusterfs-utils
Tool(s) to automate GlusterFS common / repetitive jobs

# Goal

Provide a set of tools needed to do common jobs when creating / provisioning a GlusterFS cluster and/or GlusterFS volumes.

This can help in many ways:
  * One tool thats does the work consistently across different workflows
  * No repetition of code (todays we have ansible, puppet, shell scripts and Go code implementing the same logic)
  * Easy to manage, fix issues, since its in 1 place/repo

Optionally provide ability to choose the backend (shell script, python module, ansible playbook) for running the job.
This can help choose the right backend for the right (maybe constrained) environment.


# Common / Repetitive job examples:
  * Prepping a raw block device to be used as a brick
    * Input: raw block device (eg: /dev/sda)
    * Output: /dev/sda prepped to be used as a glusterfs brick, optionally mounting it, can be enhanced to prep brick based on the workload type (future)
    * Usecases: docker/k8s workflow, openshift, heketi, OSP-d (once it supports provisioning gluster storage) et. al

  * Setting the right selinux labels
    * Input: brick mountpoint
    * Output: the brick dir is setup with the right selinux labels and perms
    * Usecases: anyplace which serves storage via GlusterFS

  * Editing glusterd.vol
    * Input: glusterd.vol path (defaults to standard path)
    * Output: glusterd.vol modified with option transport.socket.bind-address , option rpc-auth-allow-insecure, et. al
    * Usecases: Container workflow, libgfapi based workflow, in general provide a way to edit glusterd.vol using a cli tool.
