# Ceph Install

## Step 0: TLDR Rook 

1. `git clone --single-branch --branch release-1.7 https://github.com/rook/rook.git`
1. `cd rook/cluster/examples/kubernetes/ceph`
1. `kubectl create -f crds.yaml -f common.yaml -f operator.yaml`
1. `kubectl create -f cluster.yaml`