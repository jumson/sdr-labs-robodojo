# 4binder
FROM jupyter/scipy-notebook:8ccdfc1da8d5
# 
# doing ROOT stuff
USER root
ARG NB_USER
ARG NB_UID
ENV USER ${NB_USER}
ENV HOME /home/${NB_USER}
WORKDIR ${HOME}
ENV PATH $PATH:${HOME}/.local/bin
RUN echo '$USER ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers 

USER root
COPY . ${HOME}
RUN chown -R ${NB_UID} ${HOME} 
USER ${NB_USER}

# RUN pip freeze > pythonStuff.txt
# RUN conda env export -f conda.export.txt
# Specify the default command to run
CMD ["jupyter", "notebook", "--ip", "0.0.0.0"]

# docker build . -t jumson/jupyter2:base -t jumson/jupyter2:006
# run from top level of my git repo
# docker run -d -v `pwd`:/home/jovyan/notes -p 8888:8888 jumson/jupyter2:006
# docker logs CONTAINER (to find the token)
# run without '-d' when using as systemctl systemd service control
