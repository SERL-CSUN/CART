## Run Jupyter Notebooks inside Docker

1. First run the Nvidia NGC pytorch docker image

```sh
sudo docker run --gpus=all --rm -it -v $PWD:/TensorRT --net=host --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 nvcr.io/nvidia/pytorch:22.08-py3 bash
```

then go to the notebooks directory inside the docker

```sh
cd /workspace/examples/torch_tensorrt/notebooks
```

Next, Once you have entered the appropriate ```notebooks``` directory, start Jupyter with

```sh
root@arcs-base:/workspace/examples/torch_tensorrt/notebooks# jupyter notebook --allow-root --ip 0.0.0.0 --port 8888
```


Note: all the above commands are written in the README.md inside the notebooks directory.

At this point, you should be able to see the following output:

```
[I 07:38:08.359 NotebookApp] jupyter_tensorboard extension loaded.
[I 07:38:09.328 NotebookApp] JupyterLab extension loaded from /opt/conda/lib/python3.8/site-packages/jupyterlab
[I 07:38:09.328 NotebookApp] JupyterLab application directory is /opt/conda/share/jupyter/lab
[I 07:38:09.338 NotebookApp] [Jupytext Server Extension] NotebookApp.contents_manager_class is (a subclass of) jupytext.TextFileContentsManager already - OK
[I 07:38:09.339 NotebookApp] Serving notebooks from local directory: /opt/pytorch/torch_tensorrt/notebooks
[I 07:38:09.340 NotebookApp] Jupyter Notebook 6.4.10 is running at:
[I 07:38:09.340 NotebookApp] http://hostname:8888/?token=99459696da52446c6823daa9a89e7e0efc2b7ff24d0ee9b0
[I 07:38:09.340 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 07:38:09.352 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///root/.local/share/jupyter/runtime/nbserver-465-open.html
    Or copy and paste this URL:
        http://hostname:8888/?token=99459696da52446c6823daa9a89e7e0efc2b7ff24d0ee9b0

```

Copy-paste the last link in the browser. 

then replace the word `hostname:8888` from the above link to `localhost:8888`.

eg: `http://localhost:8888/notebooks/Resnet50-example.ipynb`

Your Jupyter  Notenook should now be up and running.

You can just run the cells in the notebook like you normally do.

