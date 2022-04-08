FROM cuahsi/singleuser-base:2022.04.04

USER root

RUN sudo apt install ca-certificates

RUN apt-get update && \
    rm -rf /var/lib/apt/lists/*

USER $NB_UID

ENV XDG_CACHE_HOME /home/$NB_USER/.cache/

# pull over environment file for conda
COPY environment.yml /home/jovyan/environment.yml

RUN  conda env create -f /home/jovyan/environment.yml

# add binaries to the path
ENV PATH="./binaries:${PATH}"


# Import matplotlib the first time to build the font cache.
RUN MPLBACKEND=Agg python -c "import matplotlib.pyplot" && \
    fix-permissions /home/$NB_USER

USER root
RUN apt update && apt install -y cmake \
&& rm -rf /var/lib/apt/lists/*


# Set GDAL and Proj env vars. This is necessary to ensure gdal commands don't error out when the base
# conda environment is not explicitly activated.
# see https://gis.stackexchange.com/questions/326968/ogr2ogr-error-1-proj-pj-obj-create-cannot-find-proj-db
ENV GDAL_DATA=/opt/conda/share/gdal \
    PROJ_LIB=/opt/conda/share/proj

## quick update of ipykernel
RUN pip install --upgrade ipykernel

## install system monitor
#RUN pip install nbresuse==0.3.3 \
#&& jupyter labextension install jupyterlab-topbar-extension jupyterlab-system-monitor

# get the class materials from github
#RUN git clone --depth 1 https://github.com/jdhughes-usgs/iah2021-brazil-mf6.git /opt/iah2021-brazil-mf6 \
#&& chmod -R 777 /opt/iah2021-brazil-mf6

#COPY setup_files.py /home/jovyan/setup_files.py

#ENV PYTHONPATH="${PYTHONPATH}:/opt/iah2021-brazil-mf6/python_packages"

RUN rm -rf XDG_CACHE_HOME/*
USER $NB_UID

