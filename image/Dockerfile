#
# thomasweise/docker-pandoc-r
#
# This is an image with a basic TeX Live installation,
# pandoc, calibre, and R, with some useful R packages.
# Source: https://github.com/thomasWeise/docker-pandoc-r/
# License: GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
# The license applies to the way the image is built, while the
# software components inside the image are under the respective
# licenses chosen by their respective copyright holders.
#
FROM thomasweise/docker-pandoc-calibre
MAINTAINER Thomas Weise <tweise@hfuu.edu.cn>

ENV R_REPOS="c(\"http://cran.us.r-project.org\", \"http://cran.uk.r-project.org\",  \"http://mirrors.ustc.edu.cn/CRAN\", \"http://cran.wu.ac.at/\", \"http://cran.utstat.utoronto.ca/\", \"http://cran.rstudio.com/\", \"https://cran.uni-muenster.de/\", \"http://ftp.iitm.ac.in/cran/\")"

ENV R_LIB_DIR="/usr/local/lib/R/site-library"

# do all the installation
RUN cd /tmp/ &&\
    apt-get update &&\
    apt-get install -f -y --no-install-recommends \
      libxml2-dev \
      libssl-dev \
      libcurl4-openssl-dev \
      r-base \
      r-base-dev &&\
# install the required R packages
    R_params="repos=${R_REPOS}, dependencies=TRUE, clean=TRUE" &&\
    Rscript -e "update.packages(ask=FALSE, ${R_params})" &&\
    Rscript -e "if(!(require(\"callr\"))) install.packages(\"callr\", ${R_params})" &&\
    Rscript -e "if(!(require(\"devtools\"))) install.packages(\"devtools\", ${R_params})" &&\
    Rscript -e "if(!(require(\"devtools\"))) { q(status=1L); }" &&\
# delete not needed R stuff
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/doc/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/help/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/example[s]*/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/demo/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/html/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/htmlwidgets/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/tinytest/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/NEWS\.md" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/NEWS\.Rd" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/NEWS" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/AUTHORS" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/CITATION" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/rstudioapi/.*" -delete || true &&\
    find $R_LIB_DIR -type f -regex "$R_LIB_DIR/BH/include/boost/winapi/.*" -delete || true &&\
    find $R_LIB_DIR -type f -empty -delete || true &&\
    find $R_LIB_DIR -type d -empty -delete || true &&\
    find /usr/share/R -type f -name "READM*" -delete || true &&\
    find /usr/share/R -type f -empty -delete || true &&\
    find /usr/share/R -type d -empty -delete || true &&\
# cleanup
    apt-get clean -y &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_* &&\
    rm -rf /usr/share/man &&\
    mkdir -p /usr/share/man &&\
    find /usr/share/doc -depth -type f ! -name copyright -delete &&\
    find /usr/share/doc -type f -name "*.pdf" -delete &&\
    find /usr/share/doc -type f -name "*.gz" -delete &&\
    find /usr/share/doc -type f -name "*.tex" -delete &&\
    find /usr/share/doc -type d -empty -delete || true &&\
    mkdir -p /usr/share/doc &&\
    mkdir -p /usr/share/info
