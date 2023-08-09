# Docker Container 

nerdctl features and commands are almost identical as Docker CLI. nerdctl also supports several cutting-edge features of containerd that are not present in Docker. nerdctl supports features like, lazy-pulling (stargz) and running encrypted images (ocicrypt) which are not yet supported with Docker CLI.

How to install buidkitd on Centos 7.9

1. Download binaries using Firefox on Virtual Machine OR wget file

   Open Firefox Browser and copy-paste the below URL

   https://github.com/moby/buildkit/releases/download/v0.12.1/buildkit-v0.12.1.linux-amd64.tar.gz

   OR

   wget https://github.com/moby/buildkit/releases/download/v0.12.1/buildkit-v0.12.1.linux-amd64.tar.gz

3. Extract binaries and move under /usr/local/bin directory

   su - centos

   cd Downloads

   tar -xvzf buildkit-v0.12.1.linux-amd64.tar.gz 

   sudo su -

    cp -pr /home/centos/Downloads/bin/* /usr/local/bin/

4. Start service buildkitd

    sudo buildkitd

    OR

    nohup buildkitd  &                               

5. Open new terminal and run command

    login as the root user

    cd /tmp; mkdir ctx; touch Dockerfile

    vi Dockerfile
   
    FROM oraclelinux:8
    :wq
    
6. Execute the below command to test the "nerdctl build" command

    nerdctl build -t foo /tmp/ctx


7. Reference :  https://github.com/moby/buildkit






