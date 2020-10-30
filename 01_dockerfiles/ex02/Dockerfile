# docker build -t ft-rails:on-build .
# docker build -t ex02 .
# docker run -it --rm -p 3000:3000 ex02
FROM ruby
RUN apt-get update -y && apt-get install -y build-essential libpq-dev nodejs sqlite3
ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle update --bundler
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed