FROM alpine:3.19.1

RUN apk update && apk upgrade && apk add bash wget libstdc++ icu-libs tzdata

WORKDIR /opt
RUN wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh && chmod +x ./dotnet-install.sh
RUN ./dotnet-install.sh --channel 8.0 --install-dir /opt/.dotnet/ --runtime aspnetcore

ENV DOTNET_ROOT=/opt/.dotnet
ENV PATH=$PATH:$DOTNET_ROOT:$DOTNET_ROOT/tools

ENV TZ=America/Lima
RUN cp /usr/share/zoneinfo/America/Lima /etc/localtime

WORKDIR /usr/local

RUN apk add curl
RUN curl https://download.newrelic.com/dot_net_agent/latest_release/newrelic-dotnet-agent_10.23.0_amd64.tar.gz -o newrelic-dotnet-agent_10.23.0_amd64.tar.gz
RUN tar -zxvf newrelic-dotnet-agent_10.23.0_amd64.tar.gz

ENV CORECLR_ENABLE_PROFILING=1 \
CORECLR_PROFILER={36032161-FFC0-4B61-B559-F6C5D41BAE5A} \
CORECLR_NEWRELIC_HOME=/usr/local/newrelic-dotnet-agent \
CORECLR_PROFILER_PATH=/usr/local/newrelic-dotnet-agent/libNewRelicProfiler.so \
NEW_RELIC_LICENSE_KEY=8275f66d1cbe5bed69f92c469688d4e4FFFFNRAL

WORKDIR /app
