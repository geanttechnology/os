# RancherOS

[![Build Status](https://drone-pr.rancher.io/api/badges/rancher/os/status.svg?branch=master)](https://drone-pr.rancher.io/rancher/os)
[![Docker Pulls](https://img.shields.io/docker/pulls/rancher/os.svg)](https://store.docker.com/community/images/rancher/os)
[![Go Report Card](https://goreportcard.com/badge/github.com/rancher/os)](https://goreportcard.com/badge/github.com/rancher/os)

The smallest, easiest way to run Docker in production at scale.  Everything in RancherOS is a container managed by Docker.  This includes system services such as udev and rsyslog.  RancherOS includes only the bare minimum amount of software needed to run Docker.  This keeps the binary download of RancherOS very small.  Everything else can be pulled in dynamically through Docker.

## How this works

Everything in RancherOS is a Docker container.  We accomplish this by launching two instances of
Docker.  One is what we call the system Docker which runs as the first process.  System Docker then launches
a container that runs the user Docker.  The user Docker is then the instance that gets primarily
used to create containers.  We created this separation because it seemed logical and also
it would really be bad if somebody did `docker rm -f $(docker ps -qa)` and deleted the entire OS.

![How it works](./rancheros.png "How it works")

## Release

- **v1.5.6 - Docker 19.03.11 - Linux 4.14.138**

### ISO

- https://releases.rancher.com/os/v1.5.6/rancheros.iso
- https://releases.rancher.com/os/v1.5.6/hyperv/rancheros.iso
- https://releases.rancher.com/os/v1.5.6/4glte/rancheros.iso
- https://releases.rancher.com/os/v1.5.6/vmware/rancheros.iso

#### Special docker-machine Links

- https://releases.rancher.com/os/v1.5.6/vmware/rancheros-autoformat.iso
- https://releases.rancher.com/os/v1.5.6/proxmoxve/rancheros-autoformat.iso

### Additional Downloads

#### AMD64 Links

* https://releases.rancher.com/os/v1.5.6/initrd
* https://releases.rancher.com/os/v1.5.6/vmlinuz
* https://releases.rancher.com/os/v1.5.6/rancheros.ipxe
* https://releases.rancher.com/os/v1.5.6/rootfs.tar.gz

#### Cloud Links

* https://releases.rancher.com/os/v1.5.6/rancheros-gce.tar.gz

#### VMware Links

* https://releases.rancher.com/os/v1.5.6/vmware/initrd
* https://releases.rancher.com/os/v1.5.6/vmware/rancheros.vmdk
* https://releases.rancher.com/os/v1.5.6/vmware/rootfs.tar.gz

#### Hyper-V Links

* https://releases.rancher.com/os/v1.5.6/hyperv/initrd
* https://releases.rancher.com/os/v1.5.6/hyperv/rootfs.tar.gz

#### Proxmox VE Links

* https://releases.rancher.com/os/v1.5.6/proxmoxve/initrd
* https://releases.rancher.com/os/v1.5.6/proxmoxve/rootfs.tar.gz

#### 4G-LTE Links

* https://releases.rancher.com/os/v1.5.6/4glte/initrd
* https://releases.rancher.com/os/v1.5.6/4glte/rootfs.tar.gz

**Note**:
1. you can use `http` instead of `https` in the above URLs, e.g. for iPXE.
2. you can use `latest` instead of `v1.5.6` in the above URLs if you want to get the latest version.

### Amazon

SSH keys are added to the **`rancher`** user, so you must log in using the **rancher** user.

**HVM**

Region | Type | AMI
-------|------|------
eu-north-1 | HVM | [ami-0b28754e9e36e8e07](https://eu-north-1.console.aws.amazon.com/ec2/home?region=eu-north-1#launchInstanceWizard:ami=ami-0b28754e9e36e8e07)
ap-south-1 | HVM | [ami-0a8d6fd80f6647904](https://ap-south-1.console.aws.amazon.com/ec2/home?region=ap-south-1#launchInstanceWizard:ami=ami-0a8d6fd80f6647904)
eu-west-3 | HVM | [ami-0a20d2e00be3ce551](https://eu-west-3.console.aws.amazon.com/ec2/home?region=eu-west-3#launchInstanceWizard:ami=ami-0a20d2e00be3ce551)
eu-west-2 | HVM | [ami-00d503d7ef22da04a](https://eu-west-2.console.aws.amazon.com/ec2/home?region=eu-west-2#launchInstanceWizard:ami=ami-00d503d7ef22da04a)
eu-west-1 | HVM | [ami-01e9e007e7af05e9f](https://eu-west-1.console.aws.amazon.com/ec2/home?region=eu-west-1#launchInstanceWizard:ami=ami-01e9e007e7af05e9f)
ap-northeast-2 | HVM | [ami-0798c48ba8aad886b](https://ap-northeast-2.console.aws.amazon.com/ec2/home?region=ap-northeast-2#launchInstanceWizard:ami=ami-0798c48ba8aad886b)
ap-northeast-1 | HVM | [ami-0a251d44dc78b0f2f](https://ap-northeast-1.console.aws.amazon.com/ec2/home?region=ap-northeast-1#launchInstanceWizard:ami=ami-0a251d44dc78b0f2f)
sa-east-1 | HVM | [ami-0726b3d19b7868934](https://sa-east-1.console.aws.amazon.com/ec2/home?region=sa-east-1#launchInstanceWizard:ami=ami-0726b3d19b7868934)
ca-central-1 | HVM | [ami-0eccf03e8527335c9](https://ca-central-1.console.aws.amazon.com/ec2/home?region=ca-central-1#launchInstanceWizard:ami=ami-0eccf03e8527335c9)
ap-southeast-1 | HVM | [ami-0782dcdedcc2aaa11](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#launchInstanceWizard:ami=ami-0782dcdedcc2aaa11)
ap-southeast-2 | HVM | [ami-03f9ce52431a00706](https://ap-southeast-2.console.aws.amazon.com/ec2/home?region=ap-southeast-2#launchInstanceWizard:ami=ami-03f9ce52431a00706)
eu-central-1 | HVM | [ami-0b63175a9bbbcda85](https://eu-central-1.console.aws.amazon.com/ec2/home?region=eu-central-1#launchInstanceWizard:ami=ami-0b63175a9bbbcda85)
us-east-1 | HVM | [ami-0e8a3347e4c5959bd](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#launchInstanceWizard:ami=ami-0e8a3347e4c5959bd)
us-east-2 | HVM | [ami-08faee1387289d316](https://us-east-2.console.aws.amazon.com/ec2/home?region=us-east-2#launchInstanceWizard:ami=ami-08faee1387289d316)
us-west-1 | HVM | [ami-030a2ddc7ac6017e4](https://us-west-1.console.aws.amazon.com/ec2/home?region=us-west-1#launchInstanceWizard:ami=ami-030a2ddc7ac6017e4)
us-west-2 | HVM | [ami-0fb650eb46d1c240f](https://us-west-2.console.aws.amazon.com/ec2/home?region=us-west-2#launchInstanceWizard:ami=ami-0fb650eb46d1c240f)

Additionally, images are available with support for Amazon EC2 Container Service (ECS) [here](https://rancher.com/docs/os/v1.x/en/installation/amazon-ecs/#amazon-ecs-enabled-amis).

### Azure

You can get RancherOS in the [Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/rancher.rancheros), currently only the `rancher` user can be logged in through SSH keys.

## Documentation for RancherOS

Please refer to our [RancherOS Documentation](https://rancher.com/docs/os/v1.x/en/) website to read all about RancherOS. It has detailed information on how RancherOS works, getting-started and other details.

## Support, Discussion, and Community
If you need any help with RancherOS or Rancher, please join us at either our [Rancher forums](http://forums.rancher.com) or [#rancher IRC channel](http://webchat.freenode.net/?channels=rancher) where most of our team hangs out at.

For security issues, please email security@rancher.com instead of posting a public issue in GitHub.  You may (but are not required to) use the GPG key located on [Keybase](https://keybase.io/rancher).


Please submit any **RancherOS** bugs, issues, and feature requests to [rancher/os](//github.com/rancher/os/issues).

Please submit any **Rancher** bugs, issues, and feature requests to [rancher/rancher](//github.com/rancher/rancher/issues).

## License

Copyright (c) 2014-2019 [Rancher Labs, Inc.](http://rancher.com)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
