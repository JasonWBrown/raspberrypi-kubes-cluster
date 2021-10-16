# Install K3

## Step 0: Set up master 

1. `curl -sfL https://get.k3s.io | sh -s -`

## Step 1: Set up worker

1. curl -sfL https://get.k3s.io | K3S_TOKEN="SOME_TOKEN" K3S_URL="SOME_URL" K3S_NODE_NAME="SOME_NAME" sh -

## Step 2: Set up kubeconfig

1. Copy kubeconfig from master node
1. Determine its location by running any kubectl command with `-v=6` flag
1. cat the file
1. copy to any system
1. create the file in the `~/.kube/config` location
1. point to the correct master server location

## Step 3:  Set up hostnames in etc/hosts

example
```
127.0.0.1 localhost
10.7.2.202 node1 node1
10.7.2.201 node2 node2
```

## Step 4: Reboot 

1. sudo reboot

# Issues:

## DNS with K3s. 
 Pods on Master NODE can resolve google.com but Pods on Worker Nodes can not even when the HOST can.

Work Around. Need to debug this issue more. The current situation is not ideal.  Although this is scriptable, I don't like not knowing why this is happening or a way to trouble shoot it. 

1. run command on all nodes. `iptables -F && iptables -t nat -F && iptables -t mangle -F && iptables -X`
1. set k3-agents env to a known resolv.conf file.
 ```
  > sudo nano /etc/systemd/system/k3s-agent.service.env
  # add the line
  K3S_RESOLV_CONF=/run/systemd/resolve/resolv.conf
  
  > systemctl service restart k3s-agent
 ``` 
3. add a coreDNS pod on each node???    

## Docker
Docker containers are not visible using the docker ps -a command on the host.  
