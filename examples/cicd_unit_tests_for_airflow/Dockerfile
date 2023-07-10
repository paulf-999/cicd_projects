# Base image
FROM airflow:2.2.5

# Set the working directory inside the container
WORKDIR /app

LABEL name="baseline_ubuntu_image"
LABEL desc="Baseline Ubuntu Docker image"
LABEL version="1.0"

ENV APT_GET_INSTALL_CMD="apt-get -y install --no-install-recommends"
# GDAL env vars, compilation settings
ENV CPLUS_INCLUDE_PATH /usr/include/gdal
ENV C_INCLUDE_PATH /usr/include/gdal

# Install dependencies (if applicable)
RUN set -ex; \
    apt-get -yqq update; \
    $APT_GET_INSTALL_CMD build-essential=12.8ubuntu1.1; \
    $APT_GET_INSTALL_CMD git=1:2.25.1-1ubuntu3.11; \
    $APT_GET_INSTALL_CMD python3-pip=20.0.2-5ubuntu1.9; \
    $APT_GET_INSTALL_CMD wget=1.20.3-1ubuntu2; \
    $APT_GET_INSTALL_CMD less=551-1ubuntu0.1; \
    $APT_GET_INSTALL_CMD unzip=6.0-25ubuntu1.1; \
    $APT_GET_INSTALL_CMD vim=2:8.1.2269-1ubuntu5.15; \
    #
    $APT_GET_INSTALL_CMD gettext-base; \
    $APT_GET_INSTALL_CMD openjdk-11-jre; \
    $APT_GET_INSTALL_CMD groff; \
    $APT_GET_INSTALL_CMD gdal-bin; \
    $APT_GET_INSTALL_CMD libgdal-dev; \
    $APT_GET_INSTALL_CMD gcc; \
    $APT_GET_INSTALL_CMD g++; \
    $APT_GET_INSTALL_CMD gnupg; \
    apt-get autoremove -yqq --purge; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*
# the last command is used to clean up the apt cache & helps to keep the image size down

# Copy the project files into the container
COPY requirements.txt /app

# Make sure we are using latest pip
RUN set -ex; \
    pip install --upgrade pip==23.1.2 --no-cache-dir; \
    pip install -r requirements.txt --no-cache-dir; \
    pip install 'setuptools<58.0.0' --no-cache-dir; \
    pip install 'GDAL<3.0' --no-cache-dir; \
    pip install --upgrade requests --no-cache-dir;

# add $AIRFLOW_HOME, dags dir and airflow_aac_v1 dir to PYTHONPATH
ENV PYTHONPATH=$AIRFLOW_HOME/:$AIRFLOW_HOME/dags:$AIRFLOW_HOME/

# Expose any necessary ports
EXPOSE 80/tcp
