---
title: Jupyter
parent: Tools
nav_order: 2
---


Jupyter Notebook and JupyterLab are installed in the Anaconda `base` environment. The following example uses SSH port forwarding (`ssh -L`) to access Jupyter securely from your local machine.

## Running Jupyter on Nanhu

If you are using the `base` environment, run:

```bash
jupyter-lab --no-browser --port 10086
```

To use Jupyter Notebook instead, run:

```bash
jupyter notebook --no-browser --port 10086
```

You may choose another unused, unprivileged port (generally any port above `1024`), or omit the `--port` option and let Jupyter select one.

If Jupyter is successfully launched, you will see messages like:

```text
To access the server, open this file in a browser:
    file:///home/zwshao/.local/share/jupyter/runtime/jpserver-141598-open.html
Or copy and paste one of these URLs:
    http://localhost:10086/lab?token=<token>
 or http://127.0.0.1:10086/lab?token=<token>
```

To run Jupyter from another virtual environment, activate that environment and install Jupyter in it. If you only need to use another environment as a kernel, follow the instructions in [Adding Another Virtual Environment to Jupyter](#adding-another-virtual-environment-to-jupyter).

## SSH Port Forwarding

Open another terminal on your local machine, run:

```bash
ssh -L localport:localhost:10086 zwshao@nanhu_ip
```

Replace `zwshao` with your username, `nanhu_ip` with the Nanhu IP address, and `localport` with an unused port on your local machine. For convenience, you can use the same local and remote port (`10086` in this example):

```bash
ssh -L 10086:localhost:10086 <username>@<nanhu_ip>
```

After logging in with the command above, copy the `http://127.0.0.1:10086/...` URL printed by Jupyter into a browser on your local machine. The URL contains a temporary access token; do not share it.

## Adding Another Virtual Environment to Jupyter

Install the `ipykernel` package in the virtual environment you want to use.

Assume that you have created and activated an environment named `MYENV`.

To install `ipykernel`, run:

```bash
conda install ipykernel
```

or:

```bash
pip install ipykernel
```

Then register the environment as a Jupyter kernel:

```bash
python -m ipykernel install --user --name MYENV --display-name "MYENV"
```

The `MYENV` environment will then appear as `MYENV` in Jupyter's kernel list.

## References

More information can be found at [gravity-doc](https://gravity-doc.github.io/tools/jupyter.html).
