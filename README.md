# gitlab-ci-test

owen gitlab ci test repo

## Step

1. Create a EC2 runner instance 
2. Install gitlab runner on instance 
3. Register runner with my gitlab account
4. Add .gitlab-ci.yaml to repo , run the lab and test ci flow.

## template
- trigger-gitlab-ci.yml
  - 觸發其他 gitlab 下的 repo pipeline 用的 template
- parameter-condition-gitlab-ci.yml
  - 被觸發的 pipeline job 樣本，可以透過 pass 參數來指定 job 執行或不執行
- docker-executor-ci.yml
  - 有 dind 的使用方式，以及透過 local mapping 的方式做到 persistent dependencies caching

## conf-template
- cache-template 的 volume 參數
  - 新增 `/home/gitlab-runner/.m2:/root/.m2` 為了將每次在 maven 容器裡構建時下載的 dependencies 透過 mapping 的方式 persistent 在 local 讓它可以永久 cache
- dind-template 的 volume 參數
  - 新增 `/var/run/docker.sock:/var/run/docker.sock` 為了能讓 docker 內部透過 socket binding 方式訪問 local 的 docker daemon 進行 Dockerfile 構建
  - 新增 `/home/gitlab-runner/.docker:/root/.docker` 推送到私有 registry 時，可以在 docker 內部直接引用該檔案向 registry 做驗證並推送 image