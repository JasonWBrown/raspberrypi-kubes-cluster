# Install Docker

## Helpful Links

Good resource: https://github.com/speedwing/cardano-staking-pool-edu/blob/master/DOCKER.md

# Step 0: Setup CGROUP

1. Find cmdline.txt
1. Add `cgroup_memory=1 cgroup_enable=memory` to line one
1. Reboot pi

# Step 1: Install Docker

1. `sudo snap install docker`

# Step 2: Create Docker Group and Assign Ubuntu User to it

1. `sudo addgroup --system docker`
1. `sudo adduser ubuntu docker`
1. `newgrp docker`

# Step 3: Restart Docker

1. `sudo snap disable docker`
1. `sudo snap enable docker`


# Step 4: Just because Reboot

1. `sudo reboot`



