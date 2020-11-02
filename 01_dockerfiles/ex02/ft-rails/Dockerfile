# mkdir ft-rails/ 
# mv Dockerfile ft-rails/
# vim Dockerfile
# FROM ft-rails:on-build /EXPOSE 3000 /CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]

# git clone https://bitbucket.org/railstutorial/sample_app_4th_ed.git app
# docker build -t ft-rails:on-build .
# cd ..
# docker build -t ex02 .
# docker run -it --rm -p 3000:3000 ex02
# docker-machine ip Char :3000
FROM ruby

RUN apt-get update && apt-get install -y gem build-essential libpq-dev nodejs sqlite3
RUN gem install bundler
RUN gem install rails -v 5.1.6
RUN gem install rake -v 12.3.1

#RUN apt-get update && apt-get install -y yarn

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle update --bundler
ONBUILD RUN bundle install
ONBUILD RUN rake _12.3.1_ db:migrate
ONBUILD RUN rake _12.3.1_ db:seed

ONBUILD EXPOSE 3000

