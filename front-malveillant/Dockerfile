FROM node:23-alpine3.20 AS pre-build
LABEL authors="wallace"

WORKDIR /app
COPY . .
RUN npm i && npm run build

FROM node:23-alpine3.20

WORKDIR /app
COPY --from=pre-build /app/dist ./dist
RUN npm install serve
EXPOSE 3000

CMD ["npx", "serve", "-s", "dist"]
