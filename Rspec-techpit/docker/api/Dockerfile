FROM ruby:3.1.1
ENV APP_NAME=myapp
ENV USER_NAME=myuser
ENV TZ=Asia/Tokyo
ENV RUBYGEMS_VERSION=3.3.10


WORKDIR /${APP_NAME}

COPY Gemfile Gemfile.lock /${APP_NAME}
RUN gem update --system ${RUBYGEMS_VERSION} && \
    bundle install

COPY /docker/api/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

RUN adduser ${USER_NAME} && \
    chown -R ${USER_NAME} /${APP_NAME} && \
    chown -R ${USER_NAME} ${GEM_HOME}
USER ${USER_NAME}

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]

