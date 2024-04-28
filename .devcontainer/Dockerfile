FROM elixir:1.15.7-alpine

# Build Args
ARG PHOENIX_VERSION=1.7.11

# Dependencies
RUN apk update \
  && apk upgrade \
  && apk add bash curl git inotify-tools  \
  && apk add build-base
# Phoenix
RUN mix local.hex --force \
  && mix archive.install --force hex phx_new ${PHOENIX_VERSION} \
  && mix local.rebar --force

# App Directory
ENV APP_HOME /app
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

# App Port
EXPOSE 4000

# Default Command
CMD ["mix", "phx.server"]
