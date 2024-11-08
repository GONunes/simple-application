FROM node:lts AS build
WORKDIR /app
COPY ./front/package*.json ./
RUN npm install
COPY ./front .
RUN npm run build

#-----------------------------------------------------------------------------------------------------------------------

FROM node:lts-slim
RUN npm install -g http-server
WORKDIR /app
COPY --from=build /app/dist /app
CMD ["http-server", "-p", "5000"]

