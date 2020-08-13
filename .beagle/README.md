# build

```bash
docker run --rm -it \
-v $PWD/:/go/src/github.com/mengkzhaoyun/kiali-ui \
-v /usr/local/share/.cache/yarn:/usr/local/share/.cache/yarn \
-e PUPPETEER_DOWNLOAD_HOST=https://npm.taobao.org/mirrors \
-e KIALI_ENV=production \
registry.cn-qingdao.aliyuncs.com/wod/node:12.18.3-buster \
bash

export PUPPETEER_DOWNLOAD_HOST=https://npm.taobao.org/mirrors \
KIALI_ENV=production && \
yarn && \
yarn build
```
