# fvs-workspace

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/Vibrant-Planet-Open-Science/fvs-workspace/main?urlpath=lab)

A ready-to-run workspace for the Forest Vegetation Simulator (FVS): JupyterLab with the FVS graphical interface (FVSOnLocal), the FVS executables for every US variant, and R and Python notebooks that run FVS through [`rFVS`](https://github.com/USDAForestService/ForestVegetationSimulator-Interface) and [`fvs2py`](https://github.com/Vibrant-Planet-Open-Science/fvs2py). Use it in the cloud on Binder, or on your own computer with Docker. 

This project was designed to make it easier to access the latest versions of FVS software from any operating system. Over time, we will add new learning resources that provide illustrative workflows for getting started with FVS from the GUI, from R (with `rFVS`), and from Python (with `fvs2py`). Have a workflow to share? See [CONTRIBUTING.md](CONTRIBUTING.md).

## Run it in the cloud on Binder

Click the **Binder** badge above. You'll get a JupyterLab session running on [mybinder.org](https://mybinder.org). Click the **FVS GUI** tile on the Launcher page to open the FVS GUI, or start an R or Python notebook. Binder sessions are temporary, so download anything you want to keep before the session ends.

## Run it on your computer with Docker

The image is `ghcr.io/vibrant-planet-open-science/fvs-workspace`, published for linux/amd64 and linux/arm64, so it runs natively on Windows, Mac and Linux. If you don't have it already, you'll need to install [Docker Desktop](https://www.docker.com/products/docker-desktop/) (Windows or Mac) or [Docker Engine](https://docs.docker.com/engine/install/) (Linux), and start it.

Once you have Docker running, open a terminal: **PowerShell** on Windows, **Terminal** on Mac or Linux.

If you are on Linux, you'll need to create the two folders where your work is saved and let FVS write to them using the following command. On Windows and Mac, Docker creates them for you, so you don't have to worry about this.

```
mkdir -p fvs-work fvs-projects && chmod 777 fvs-work fvs-projects
```

You can then run the Docker container. The first time you do this, Docker fetches the fvs-workspace image from the GitHub Container Registry (about 1 GB to download, unpacks to about 4 GB on disk). This can take several minutes. Future runs should go much faster because the image won't be re-downloaded unless the "latest" version we've published has been updated.

```
docker run --rm -p 8888:8888 -v "${PWD}/fvs-work:/home/jovyan/work" -v "${PWD}/fvs-projects:/home/jovyan/project" ghcr.io/vibrant-planet-open-science/fvs-workspace:latest
```

After you execute the `docker run` command above, you should see a link that starts with `http://127.0.0.1:8888/lab?token=`. Open that link in your web browser. You should then see a tile for the **FVS GUI** that you can use to launch it. Your work will be saved in two folders inside the folder the terminal started in:
- `fvs-projects`: your FVS GUI projects.
- `fvs-work`: notebooks and other files you save in the `work` folder in JupyterLab's file list. Anything saved outside `work` is deleted when you stop.

When you are done, to stop the Docker container you can go back to the terminal and press **Ctrl+C**.

## Versions

Each release of this repository publishes an image tagged with its version (for example `0.1.0`) and `latest`. The FVS, FVS Interface and fvs-build versions it is built from are pinned in [`.github/workflows/release-please.yml`](.github/workflows/release-please.yml). The fvs-workspace Docker image is built by [fvs-build](https://github.com/Vibrant-Planet-Open-Science/fvs-build).

## Acknowledgment and disclaimer

FVS, the FVS graphical interface (FVSOnLocal) and `rFVS` are developed and maintained by the USDA Forest Service, and this project builds on the source code and documentation the Forest Service publishes. fvs-workspace is an independent project of Vibrant Planet and is not affiliated with or endorsed by the USDA Forest Service. Any opinions, findings, conclusions, or recommendations expressed here are those of the authors and should not be construed to represent any official USDA or U.S. Government determination or policy. The use of trade or firm names is for reader information and does not imply endorsement by the U.S. Department of Agriculture of any product or service.
