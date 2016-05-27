FROM redmine:2.6.9-passenger

MAINTAINER maeda <duck8823@gmail.com> 

RUN apt-get update && \
    apt-get install -y build-essential wget unzip vim uuid-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/redmine/plugins

RUN git clone -b redmine-2.x https://github.com/alexbevi/redmine_knowledgebase.git
RUN hg clone -b redmine2.x https://bitbucket.org/nobiinu_and/redmine_hudson
RUN git clone https://github.com/backlogs/redmine_backlogs.git && \
    sed -e "s/gem \"nokogiri\"/#/g" redmine_backlogs/Gemfile > tmp && mv tmp redmine_backlogs/Gemfile
RUN git clone https://github.com/koppen/redmine_github_hook.git
RUN git clone -b v1.5.2e https://github.com/danmunn/redmine_dmsf.git

RUN gem install xapian-full-alaveteli -v "1.2.21.1"
RUN bundle install

WORKDIR /usr/src/redmine
