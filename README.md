version: 2.1jobs:  build:    docker:      - image: cimg/node:14.10.1 # the primary container, where your job's commands are run        auth:          username: mydockerhub-user          password: $DOCKERHUB_PASSWORD  # context / project UI env-var reference    steps:      - checkout # check out the code in the project directory      - run: echo "hello world" # run the `echo` command #Irie
Nft 

version: 2
jobs:
build:
  working_directory: /tmp
  steps:
    - run:
        name: Creating Dummy Artifacts
        command: |
          echo "my artifact file" > /tmp/art-1;
          mkdir /tmp/artifacts;
          echo "my artifact files in a dir" > /tmp/artifacts/art-2;

    - store_artifacts:
        path: /tmp/art-1
        destination: artifact-file

    - store_artifacts:
        path: /tmp/artifacts
