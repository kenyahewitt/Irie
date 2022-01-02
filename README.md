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
# Use the latest 2.1 version of CircleCI pipeline process engine.
# See: https://circleci.com/docs/2.0/configuration-reference
version: 2.1

# Define a job to be invoked later in a workflow.
# See: https://circleci.com/docs/2.0/configuration-reference/#jobs
jobs:
  say-hello:
    # Specify the execution environment. You can specify an image from Dockerhub or use one of our Convenience Images from CircleCI's Developer Hub.
    # See: https://circleci.com/docs/2.0/configuration-reference/#docker-machine-macos-windows-executor
    docker:
      - image: cimg/base:stable
    # Add steps to the job
    # See: https://circleci.com/docs/2.0/configuration-reference/#steps
    steps:
      - checkout
      - run:
          name: "Say hello"
          command: "echo Hello, World!"

# Invoke jobs via workflows
# See: https://circleci.com/docs/2.0/configuration-reference/#workflows
workflows:
  say-hello-workflow:
    jobs:
      - say-hello
![image](https://user-images.githubusercontent.com/83016880/147891542-ce5170ea-8807-47bc-82e8-e464a280b61a.jpg)
