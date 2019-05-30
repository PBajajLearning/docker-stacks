# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=gcr.io/univai-jupyterhub/scipy-notebook-gpu
FROM $BASE_CONTAINER

LABEL maintainer="Rahul Dave <rahuldave@univ.ai>"

# Install Tensorflow
RUN conda install --quiet --yes \
    'tensorflow-gpu=1.13*' \
    'keras=2.2*' && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

RUN conda install pytorch torchvision -c pytorch
RUN pip install tensorboardX
RUN pip install wandb

# Allow drivers installed by the nvidia-driver-installer to be located
ENV LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/nvidia/lib64
# Also, utilities like `nvidia-smi` are installed here
ENV PATH=${PATH}:/usr/local/nvidia/bin
