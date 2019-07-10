FROM continuumio/miniconda3:4.6.14

WORKDIR /opt/icepick
COPY ../binder/environment.yml /opt/icepick
RUN conda config --add channels conda-forge
RUN conda env create -f environment.yml && \
    apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/* && \
    conda clean -tipsy && conda clean --yes --all
RUN mkdir -p /opt/icepick/notebooks
COPY ./notebooks /opt/icepick/notebooks

CMD bash -c "source activate icepick; jupyter notebook --allow-root --notebook-dir=/opt/pdi-topics/notebooks --ip='0.0.0.0' --port=8888 --no-browser"
