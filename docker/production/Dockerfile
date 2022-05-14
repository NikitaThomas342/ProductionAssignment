FROM node:16.13.1-alpine3.12 as build

WORKDIR /production
COPY ./package.json /production/
COPY ./yarn.lock /production/
RUN yarn
COPY . /production
RUN yarn build

FROM nginx:1.17.8-alpine

COPY --from=build /production/build /usr/share/nginx/html

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx/nginx.conf /etc/nginx/conf.d

EXPOSE 80