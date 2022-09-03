
# DOCKER Installation and Setup in ubuntu 20.04

1. Docker install in ubuntu follwoing [this reference](https://docs.docker.com/engine/install/ubuntu/). The commands are copied to below in the order with one change in the last step.

```sh
 
 $ sudo apt-get update
 ```
```sh
 $ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

```sh
$ sudo mkdir -p /etc/apt/keyrings
```

```sh

 $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```sh
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
 ```
 
 ```sh
 $  sudo apt-get update
```

```sh
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

```sh
$ apt-cache madison docker-ce
```
The following cmd is changed as follows from the original docker docs.
```sh
$ sudo apt-get install docker
```

```sh
$ sudo docker run hello-world
```

```sh
sudo docker images
```


 
 



