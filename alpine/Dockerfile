FROM 76591745/newrelic:alpine

COPY app/publish/ /app/
ENV ASPNETCORE_URLS=http://*:5000
CMD [ "dotnet", "WeatherForecast.dll" ]
