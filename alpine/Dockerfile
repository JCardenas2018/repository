FROM 76591745/newrelic:alpine

ENV NEW_RELIC_APP_NAME="JCardenasTest"

COPY app/publish/ /app/
ENV ASPNETCORE_URLS=http://*:5000
CMD [ "dotnet", "WeatherForecast.dll" ]
