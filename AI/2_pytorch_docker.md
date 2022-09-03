## 1. Pytorch Container in Docker

Now run the follwoing command in the terminal from [this pytorch-docker reference](https://hub.docker.com/r/pytorch/pytorch) :

```sh
docker pull pytorch/pytorch
```

- Also, refere to the [official pytorch github docker-image here](https://github.com/pytorch/pytorch#docker-image).

## 2. Nvidia docker 

Note that running the pytorch docker image requires `nvidia-docker`. So we also need to install that from this reference:
- https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html

```sh
$ distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
      && curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
      && curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | \
            sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
            sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

```sh
$ sudo apt-get update

```

```sh
$ sudo apt-get install -y nvidia-docker2
```

```sh
$ sudo systemctl restart docker

```

```sh
$ sudo docker run --rm --gpus all nvidia/cuda:11.0.3-base-ubuntu20.04 nvidia-smi
```



## 3. Nvidia NGC pytorch 

- https://catalog.ngc.nvidia.com/orgs/nvidia/containers/pytorch

  Nvidia NGC pytorch docker containers
  
  ```sh
  $ sudo docker run --gpus all -it --rm nvcr.io/nvidia/pytorch:xx.xx-py3
  
  ``` 
  in place of the `xx.xx-py3` put the latest tag from the left panel on the above nvidia pytorch docker containers website.
  
  so in our case, `22.08-py3`
  ```sh
  $ sudo docker run --gpus all -it --rm nvcr.io/nvidia/pytorch:22.08-py3
  ```
  
  Note this is an important docker command which you use every time to pull the pytorch docker image. 
  
  However the first time you run it, you will find that it does not work. To make it run, we need to set the `default-runtime` as `nvidia` as descibed in this `dusty-nv jetson-containers` github repo:
  - https://github.com/dusty-nv/jetson-containers

So inser the following command in terminal:
```sh
$ sudo vim /etc/docker/daemon.json
```

And edit the file to include the following code line added by vim `i` cmd.
```
,
    "default-runtime": "nvidia"
    
```

After you are done editing the file. press `:wq` to save the file and exit. 
Note: you only do `:q` to exit `vim` editor.

Now that you have set your default-runtime as nvidia you you should see the following the whole file in the vim editor as follows:
![Image of vim default-runtime set as nvidia]()














