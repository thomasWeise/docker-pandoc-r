#
# thomasweise/docker-pandoc-r
#
# This is an image with a basic TeX Live installation,
# pandoc, and R, with some useful R packages.
# Source: https://github.com/thomasWeise/docker-pandoc-r/
# License: GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
# The license applies to the way the image is built, while the
# software components inside the image are under the respective
# licenses chosen by their respective copyright holders.
#
FROM thomasweise/docker-pandoc
MAINTAINER Thomas Weise <tweise@hfuu.edu.cn>

ENV R_REPOS="c(\"http://cran.us.r-project.org\", \"http://cran.uk.r-project.org\",  \"http://mirrors.ustc.edu.cn/CRAN\", \"http://cran.wu.ac.at/\", \"http://cran.utstat.utoronto.ca/\", \"http://cran.rstudio.com/\", \"https://cran.uni-muenster.de/\", \"http://ftp.iitm.ac.in/cran/\")"

# do all the installation
RUN cd /tmp/ &&\
    apt-get clean &&\
    apt-get update &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get update &&\
    apt-get install -f -y libxml2-dev \
                          libssl-dev \
                          libcurl4-openssl-dev \
                          r-base \
                          r-base-dev &&\
# install the required R packages
    R_params="repos=${R_REPOS}, dependencies=TRUE, clean=TRUE" &&\
    Rscript -e "update.packages(ask=FALSE, ${R_params})" &&\
    Rscript -e "if(!(require(\"callr\"))) install.packages(\"callr\", ${R_params})" &&\
    Rscript -e "if(!(require(\"devtools\"))) install.packages(\"devtools\", ${R_params})" &&\
    Rscript -e "if(!(require(\"devtools\"))) { q(-1L); }" &&\
# cleanup
    apt-get clean &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get clean &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_*
