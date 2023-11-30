#build phase
FROM node:18-alpine as builder
WORKDIR /usr/app
COPY ./package.json ./
RUN npm install
COPY ./ ./
#convert typescript files into js files
RUN npm run build 

#run phase
#build phase
FROM node:18-alpine
WORKDIR /usr/app
COPY ./package.json ./
RUN npm install
COPY --from=builder /usr/app/dist /usr/app
CMD [ "node", "server.js" ]