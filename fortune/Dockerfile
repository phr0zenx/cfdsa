#Test Docker Image
FROM node:latest
#Env Var
ENV APP_PORT=3000
ENV APP_ROOT=/app

#Execution
WORKDIR ${APP_ROOT}
ADD main.js .
ADD package-lock.json .
ADD package.json .
ADD public public
ADD views views

RUN npm i

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT}/ready > /dev/null || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node","main.js" ]
