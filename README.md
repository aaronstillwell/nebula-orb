# Nebula orb

Easily access your nebula network from a CircleCI job. 

## Requirements

* This orb currently only supports Linux.
* Much like a VPN, nebula needs the `NET_CAP_ADMIN` capability, therefore nebula needs to be used on a machine based job. Docker based jobs are not able to run nebula.
  
## Usage

```
version: 2.1

orbs:
  nebula: aaronstillwell/nebula@0.1.0

jobs:
  deploy:
    machine:
      image:
    steps:
      - checkout
      - nebula/install-and-start
      # Nebula should now be running
      - run:
          name: Ping nebula node
          command: ping 192.168.100.1
      
workflows:
  deploy:
    jobs:
      - deploy
```

