# Nebula orb

[![CircleCI Build Status](https://circleci.com/gh/aaronstillwell/nebula-orb.svg?style=shield "CircleCI Build Status")](https://circleci.com/gh/aaronstillwell/nebula-orb) [![CircleCI Orb Version](https://badges.circleci.com/orbs/aaronstillwell/nebula.svg)](https://circleci.com/orbs/registry/orb/aaronstillwell/nebula) [![GitHub License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://raw.githubusercontent.com/aaronstillwell/nebula-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/ecosystem/orbs)

Easily access your [nebula](https://github.com/slackhq/nebula) network from a CircleCI job. 

## Requirements

* This orb currently only supports Linux.
* Much like a VPN, nebula needs the `NET_CAP_ADMIN` capability, therefore nebula needs to be used on a machine based job. Docker based jobs are not able to run nebula.
  
## Usage

```
version: 2.1

orbs:
  nebula: aaronstillwell/nebula@0.1.1

jobs:
  deploy:
    machine:
      image: ubuntu-2004:202010-01
    steps:
      - checkout
      - nebula/install-and-start
      # Nebula should now be running
      - run:
          name: Access resources on nebula network
          command: curl 192.168.100.5/my-endpoint
      
workflows:
  deploy:
    jobs:
      - deploy
```

