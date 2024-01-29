FROM beetravels/node-base:v1 as ui

WORKDIR /services/ui/frontend

ENV GENERATE_SOURCEMAP=false

COPY frontend .

RUN yarn build

FROM beetravels/node-base:v1 as release

WORKDIR /services/ui/backend

COPY --from=ui /services/ui/frontend/build client/build
COPY  backend/index.js backend/doc-collector.js backend/info-collector.js backend/streamableAxios.js backend/package.json ./

EXPOSE 9000

CMD ["yarn", "node", "index.js"]
