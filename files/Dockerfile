FROM rocker/rstudio:3.6.2

RUN apt-get update && \
    apt-get -y install ruby jekyll ruby-jekyll-watch
RUN R -e "install.packages(c('checkpoint', 'dplyr', 'ggplot2', 'knitr', 'plyr', 'readr', 'remotes', 'rmarkdown', 'stringr', 'tidyr'), repos = 'http://cran.us.r-project.org')" 
WORKDIR /srv/jekyll
 
