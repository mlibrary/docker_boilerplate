FROM ruby:2.7.2
ARG UNAME=app
ARG UID=1000
ARG GID=1000

LABEL maintainer="uniqname@umich.edu"

RUN gem install bundler:2.1.4

RUN groupadd -g ${GID} -o ${UNAME}
RUN useradd -m -d /app -u ${UID} -g ${GID} -o -s /bin/bash ${UNAME}
RUN mkdir -p /gems && chown ${UID}:${GID} /gems

USER $UNAME
COPY --chown=${UID}:${GID} Gemfile* /app/

ENV BUNDLE_PATH /gems

WORKDIR /app
RUN bundle install

COPY --chown=${UID}:${GID} . /app

CMD ["tail", "-f", "/dev/null"]
