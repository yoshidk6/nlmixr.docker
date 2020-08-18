# Use tidyverse as base
FROM rocker/tidyverse:3.6.3


# Install necessary libraries
RUN apt-get update
RUN apt-get install -y wget xclip libcurl4-openssl-dev libssl-dev zlib1g-dev libudunits2-dev libxml2-dev libcairo2-dev


# Install R packages and miniconda (for python)
RUN install2.r --error --skipinstalled \
    xpose reticulate RxODE nlmixr
	
## Install miniconda

RUN sudo -u rstudio Rscript -e "reticulate::install_miniconda()"
RUN sudo -u rstudio Rscript -e "reticulate::conda_install('r-reticulate', 'sympy')"

RUN Rscript -e "devtools::install_github('nlmixrdevelopment/xpose.nlmixr')"
RUN Rscript -e "devtools::install_github('RichardHooijmaijers/shinyMixR')"


# Copy files
COPY examples /home/rstudio/examples


# Clean-up
RUN rm -rf /var/lib/apt/lists/*