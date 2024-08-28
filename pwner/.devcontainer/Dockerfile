FROM blackarchlinux/blackarch:latest

RUN pacman --noconfirm -Syu

RUN curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh" && bash Miniforge3-$(uname)-$(uname -m).sh -b
SHELL ["/root/miniforge3/bin/mamba", "run", "--no-capture-output", "/bin/bash", "-c"]
RUN mamba init

RUN mamba create -n pwn python=3.12
SHELL ["/root/miniforge3/bin/mamba", "run", "--no-capture-output", "-n", "pwn", "/bin/bash", "-c"]

RUN mamba install -y sage
RUN mamba install -y pycryptodome
RUN mamba install -y pwntools

RUN pacman --noconfirm -S git
RUN pacman --noconfirm -S ffmpeg
RUN pacman --noconfirm -S man-db

RUN cd / && git clone https://github.com/pwndbg/pwndbg && cd pwndbg && (yes | ./setup.sh)

RUN conda config --set auto_activate_base false

RUN mamba install -y tqdm
RUN mamba install -y jupyterlab
