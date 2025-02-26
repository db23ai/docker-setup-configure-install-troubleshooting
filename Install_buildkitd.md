# Docker Container 

`nerdctl` features and commands are almost identical to the Docker CLI. `nerdctl` also supports several cutting-edge features of `containerd` that are not present in Docker. `nerdctl` supports features like lazy-pulling (stargz) and running encrypted images (ocicrypt) which are not yet supported with the Docker CLI.

## How to Install `buildkitd` on CentOS 7.9

### 1. Download Binaries Using Firefox on Virtual Machine OR `wget` File

   Open Firefox Browser and copy-paste the below URL:
   
   [https://github.com/moby/buildkit/releases/download/v0.12.1/buildkit-v0.12.1.linux-amd64.tar.gz](https://github.com/moby/buildkit/releases/download/v0.12.1/buildkit-v0.12.1.linux-amd64.tar.gz)

   OR

   Use `wget`:
   ```sh
   wget https://github.com/moby/buildkit/releases/download/v0.12.1/buildkit-v0.12.1.linux-amd64.tar.gz
   ```

### 2. Extract Binaries and Move Under `/usr/local/bin` Directory

   ```sh
   su - centos
   cd Downloads
   tar -xvzf buildkit-v0.12.1.linux-amd64.tar.gz 
   sudo su -
   cp -pr /home/centos/Downloads/bin/* /usr/local/bin/
   ```

### 3. Start Service `buildkitd`

   ```sh
   nohup buildkitd &
   ```

### 4. Create Dockerfile Under `/tmp` Directory

   Login as the root user:

   ```sh
   cd /tmp
   mkdir ctx
   cd ctx
   touch Dockerfile
   vi Dockerfile
   ```

   Add the following content to the `Dockerfile`:
   ```Dockerfile
   FROM oraclelinux:8
   ```

   Save the file and exit the editor:
   ```
   :wq
   ```

### 5. Test the `nerdctl build` Command

   ```sh
   nerdctl build -t foo /tmp/ctx
   ```

## Error Solution

If you encounter the following error:
```
ERRO[0000] `buildctl` needs to be installed and `buildkitd` needs to be running, see https://github.com/moby/buildkit  error="2 errors occurred:\n\t* failed to ping to host unix:///run/buildkit-default/buildkitd.sock: exec: \"buildctl\": executable file not found in $PATH\n\t* failed to ping to host unix:///run/buildkit/buildkitd.sock: exec: \"buildctl\": executable file not found in $PATH\n\n"
FATA[0000] no buildkit host is available, tried 2 candidates: 2 errors occurred:
    * failed to ping to host unix:///run/buildkit-default/buildkitd.sock: exec: "buildctl": executable file not found in $PATH
    * failed to ping to host unix:///run/buildkit/buildkitd.sock: exec: "buildctl": executable file not found in $PATH
```

Make sure that `buildctl` is installed and `buildkitd` is running.
