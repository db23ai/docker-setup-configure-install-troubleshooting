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

    nohup buildkitd  &                               

5. Create Dockerfile under /tmp directory

    login as the root user

    cd /tmp; mkdir ctx; touch Dockerfile

    vi Dockerfile
   
    FROM oraclelinux:8

    :wq
   
    
    
7. Execute the below command to test the "nerdctl build" command

    nerdctl build -t foo /tmp/ctx


8. Reference :  https://github.com/moby/buildkit

Above solution for below Error :

nerdctl build -t foo /tmp/ctx

ERRO[0000] `buildctl` needs to be installed and `buildkitd` needs to be running, see https://github.com/moby/buildkit  error="2 errors occurred:\n\t* failed to ping to host unix:///run/buildkit-default/buildkitd.sock: exec: \"buildctl\": executable file not found in $PATH\n\t* failed to ping to host unix:///run/buildkit/buildkitd.sock: exec: \"buildctl\": executable file not found in $PATH\n\n"
FATA[0000] no buildkit host is available, tried 2 candidates: 2 errors occurred:
	* failed to ping to host unix:///run/buildkit-default/buildkitd.sock: exec: "buildctl": executable file not found in $PATH
	* failed to ping to host unix:///run/buildkit/buildkitd.sock: exec: "buildctl": executable file not found in $PATH






