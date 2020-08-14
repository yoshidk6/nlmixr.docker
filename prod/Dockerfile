# Use the r-base docker to start
FROM rocker/tidyverse:3.6.3

RUN apt-get -y update \
  && apt-get install -y \
              python3-pip python3-sympy python3-dev xclip \
              libcurl4-openssl-dev libssl-dev  zlib1g-dev libudunits2-dev libxml2-dev libcairo2-dev 

RUN ln -s $(which python3) /usr/local/bin/python

RUN install2.r --error --skipinstalled \
    xpose reticulate RxODE nlmixr
	
RUN Rscript -e "devtools::install_github('nlmixrdevelopment/xpose.nlmixr')"
RUN Rscript -e "devtools::install_github('richardhooijmaijers/shinyMixR')"

# Specfy which python to use for reticulate
# These does not help avoid miniconda installation message
#RUN echo 'reticulate::use_python("/usr/local/bin/python")' >> ~/.Rprofile
#RUN echo 'Sys.setenv(RETICULATE_PYTHON = "/usr/bin/python")' >> ~/.Rprofile

COPY examples /home/rstudio/examples
