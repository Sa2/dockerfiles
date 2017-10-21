FROM node:8.5.0-alpine
MAINTAINER Sa2 <ar-ciel_ar-dor_harvestasya@live.jp>
VOLUME 

# 必要なツールとJST化
RUN apk --update add tzdata wget curl git openssh && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apk del tzdata && \
    rm -rf /var/cache/apk/*