## Start with the official rocker image (lightweight Debian)
FROM rocker/tidyverse:4.2.1

# install preliminary requirements
RUN apt-get update -y\
    && apt-get install -y git\
    && apt-get install -y libudunits2-dev\
    && apt-get install -y libgdal-dev\
    && apt-get install -y awscli

# copy working directory
COPY . /root/pipeline-cleaning

# use the bohemia kenya work directory
WORKDIR /root/pipeline-cleaning

# use renv to replicate
RUN R -e "install.packages('renv')"
RUN R -e "renv::init(bare = TRUE)"
RUN R -e "renv::restore()"

# run all pipeline
CMD make pipeline
