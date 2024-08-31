FROM ruby:alpine

RUN apk update && apk add --no-cache alpine-sdk tree

WORKDIR /my-app

# Install gems
COPY Gemfile ./
COPY Gemfile.lock ./
RUN bundle install

# copy all the files
COPY . ./
COPY entrypoint.sh /usr/local/bin/

ENTRYPOINT [ "/usr/local/bin/entrypoint.sh" ]