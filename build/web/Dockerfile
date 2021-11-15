FROM node:16 as builder

COPY .env .

RUN mkdir /pearProject && \
    git clone -b dev https://gitee.com/vilson/vue-projectManage.git /pearProject && \
    cp .env /pearProject && \
    cd /pearProject && \
    npm install -g cnpm --registry=https://registry.npm.taobao.org && \
    cnpm install && \
    npm run build

FROM nginx

COPY --from=builder /pearProject/dist/ /usr/share/nginx/html/
