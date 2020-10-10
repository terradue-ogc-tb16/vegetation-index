FROM terradue/l1-binder:latest

MAINTAINER Terradue S.r.l

COPY . ${HOME}

USER root

RUN /opt/anaconda/bin/conda env create --file ${HOME}/environment.yml

ENV PREFIX /opt/anaconda/envs/env_vi

RUN ${PREFIX}/bin/python -m ipykernel install --name kernel

RUN chown -R ${NB_UID} ${HOME}

RUN mkdir -p /workspace/data && chown -R ${NB_UID} /workspace

USER ${NB_USER}

RUN test -f ${HOME}/postBuild && chmod 755 ${HOME}/postBuild && ${HOME}/postBuild || true

WORKDIR ${HOME}