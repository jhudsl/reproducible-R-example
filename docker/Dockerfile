FROM rocker/tidyverse:4.4
LABEL maintainer="cansav09@gmail.com"
WORKDIR /rocker-build/

# Install apt-getable packages to start
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils dialog

RUN apt-get -y --no-install-recommends install \
  python3-pip  python3-dev

# Install refine bio and dependencies
RUN pip3 install \
  "pyrate-limiter==2.10.0" \
  redis \
  pyrefinebio  --break-system-packages

# Commonly used R packages
RUN Rscript -e  "install.packages( \
    c('renv', \
      'pheatmap'))"

# Set final workdir for commands
WORKDIR /home/rstudio

ENV USER="rstudio" ROOT="TRUE"
