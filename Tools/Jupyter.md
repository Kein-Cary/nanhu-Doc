---
sort: 2
title: Jupyter
--- 

Jupyter Notebook/Jupyter Lab has been installed in the `base` environment of anaconda. One can simply run jupyter as usual and use SSH port forwarding via `ssh -L`. The following is an example.

## Running Jupyter on Nanhu
If you are using the `base` environment, simply run:
```bash
(base) zwshao@nanhu:~$ jupyter-lab --no-browser --port 10086
```
Or to use Jupyte Notebook, run:
```bash
(base) zwshao@nanhu:~$ jupyter notebook --no-browser --port 10086
```
The port number `10086` can be any number larger than `8888`. Or you can also ignore this flag and let jupyter choose one for you.

If Jupyter is successfully launched, you will see messages like:
```text
To access the server, open this file in a browser:
    file:///home/zwshao/.local/share/jupyter/runtime/jpserver-141598-open.html
Or copy and paste one of these URLs:
    http://localhost:10086/lab?token=e20a37948217ce8c4da1bfeeddfdafbd7a22795f7d43a625
 or http://127.0.0.1:10086/lab?token=e20a37948217ce8c4da1bfeeddfdafbd7a22795f7d43a625
```

If you want to use Jupyter under another virtual environment, you can switch to the other environment and install jupyter by your self. The following steps will be similar as above and below. Note that if you just want to access the packages in other environments, there is a simpler way to do this, as stated in the "Adding Other Virtual Environment into Jupyter" section below.

## SSH Port Forwarding
Open another terminal on your local machine, run:
```bash
ssh -L localport:localhost:10086 zwshao@nanhu_ip
```
Again, you can arbitrarily specify the localport number as long as it's not used by the system. But for convenience, it's better to keep it the same as the port number you specified when running Jupyter (i.e., `10086` in this case). Also, remember to replace `nanhu_ip` with the IP address we are using.

After successfully logging into Nanhu via above command, you can use your favorite browser to open the URL link above [http://127.0.0.1:10086/lab?token=e20a37948217ce8c4da1bfeeddfdafbd7a22795f7d43a625](http://127.0.0.1:10086/lab?token=e20a37948217ce8c4da1bfeeddfdafbd7a22795f7d43a625) and should be able to see the Jupyter interface.

## Adding Other Virtual Environment into Jupyter
To do so, you need `ipykernel` package installed in your virtual environment.

Assume that you have created your own virtual environment named MYENV and activated.

To install `ipykernel`, run
```bash
conda install ipykernel
```
or
```bash
pip install ipykernel
```
Then configure it using
```bash
python -m ipykernel install --user --name MYENV --display-name "abc"
```
The virtual environment MYENV will be shown as abc in your Jupyter.

## References
More information can be found at [gravity-doc](https://gravity-doc.github.io/tools/jupyter.html).
