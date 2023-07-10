# Base image
FROM airflow:2.2.5

# Set the working directory inside the container
WORKDIR /app

USER root
RUN set -ex; \
    apt-get -yqq update; \
    apt-get -yqq install --no-install-recommends vim=2:8.1.2269-1ubuntu5.15; \
    apt-get autoremove -yqq --purge; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*

USER airflow
# install additional libs
COPY ./requirements.txt /app
# COPY airflow_aac_v1 ./airflow_aac_v1
# add $AIRFLOW_HOME, dags dir and airflow_aac_v1 dir to PYTHONPATH
#ENV PYTHONPATH=$AIRFLOW_HOME/dags:$AIRFLOW_HOME/airflow_aac_v1
ENV PYTHONPATH=$AIRFLOW_HOME/:$AIRFLOW_HOME/dags:$AIRFLOW_HOME/airflow_aac_v1

RUN set -ex; \
    pip install --upgrade pip --no-cache-dir; \
    pip3 install --upgrade requests --no-cache-dir \
    pip3 install -r requirem --no-cache-dir
