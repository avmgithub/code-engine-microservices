FROM beetravels/node-base:v1 as ui
#FROM avmdocker/node-base:v3 as ui

WORKDIR /services/ui/frontend

ENV GENERATE_SOURCEMAP=false

COPY frontend .

#RUN yarn vis-network

RUN yarn build

#FROM avmdocker/node-base:v3 as release
FROM beetravels/node-base:v1 as ui

WORKDIR /services/ui/backend

COPY --from=ui /services/ui/frontend/build client/build
COPY  backend/index.js backend/doc-collector.js backend/info-collector.js backend/streamableAxios.js backend/package.json ./

EXPOSE 9000

CMD ["yarn", "node", "index.js"]
