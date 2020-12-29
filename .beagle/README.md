# git

```bash
git remote add upstream git@github.com:kiali/kiali-ui.git

git fetch upstream

git merge v1.28.0

git remote add beagle git@cloud.wodcloud.com:cloud/kiali-ui.git

git fetch beagle

git push beagle github
```

## build

```bash
docker run --rm \
-v /usr/local/share/.cache/yarn:/usr/local/share/.cache/yarn \
-v $PWD/:/go/src/github.com/kiali/kiali-ui \
-w /go/src/github.com/kiali/kiali-ui \
-e PUPPETEER_DOWNLOAD_HOST=https://npm.taobao.org/mirrors \
-e KIALI_ENV=production \
registry.cn-qingdao.aliyuncs.com/wod/devops-node:14.15.0-buster \
bash -c 'yarn install --frozen-lockfile && yarn build'
```

## cache

```bash
# dev
docker run \
--rm \
-v $PWD/:/go/src/github.com/kiali/kiali-ui \
-v $PWD/build/cache/:/cache \
-w /go/src/github.com/kiali/kiali-ui \
-e PLUGIN_REBUILD=true \
-e PLUGIN_CHECK=yarn.lock \
-e PLUGIN_MOUNT=./node_modules \
-e DRONE_COMMIT_BRANCH=github \
-e CI_WORKSPACE=/go/src/github.com/kiali/kiali-ui \
registry.cn-qingdao.aliyuncs.com/wod/devops-cache:1.0
```
