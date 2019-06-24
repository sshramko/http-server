For running this demo you need
- Docker
- AWS account
- Github account (github.com)
- Dockerhub account (dockerhub.com)
- Circleci account that attached to github account (circleci.com)


## Kublr cluster creation
1. Register on kublr.com site and get evaluation version of kublr docker image

1. Run kublr docker image  
``
sudo docker run --name kublr -d --restart=unless-stopped -p 9080:9080 -e KUBLR_LICENSE=<license key> kublr/kublr:1.12
``

1. Open localhost:9080 and login using admin/
   Select "Clusters" section and click "Add kublr platform"
1. Specify 
    - cluster name: circleci-kublr-platform
    - operation system : aws-ubuntu-16.04
    - masters: 1
    - Instance Type: t2.large
    - Full Kublr Platform Credentials: Create you password
    - Nodes Count: 2
    - Operating System: aws-ubuntu-16.04
    - Instance Type: t2.xlarge
    - Confirm and install
1. Wait while cluster will be created.

## Setup circleci
1. Create repository in dockerhub.
In this example it is kublr/demo-circleci

1. Clone demo project repository on github.

1. Go to https://circleci.com and add a new project. Select cloned project from list.
    - Operating System: linux
    - Language: Node
1. Open project settings -> Environment Variables ( in BUILD SETTINGS section)
    Add variables:
    - DOCKERHUB_USERNAME: Dockehub username
    - DOCKERHUB_PASS:	Dockerhub password
    - IMAGE_NAME : Dockerhub repository name (kublr/demo-circleci in example)
    - KUBLR_ENDPOINT: Url to kublr kluster without /, for example https://circle-ci.test.kublr-dev.com
    - KUBLR_USERNAME: kublr username
    - KUBLR_PASSWORD: kublr password
    - KUBLR_CLUSTER: Created kublr cluster name
    - KUBLR_SPACE: Kublr platform cluster namespace, usually kublr-system

1. Open circleci jobs page and run build job.

##How it works



                             
 


