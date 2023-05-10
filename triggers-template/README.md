## gitlab-ci reference 中的 trigger 參數使用
https://docs.gitlab.com/ee/ci/yaml/#trigger

### 優點/缺點

優點   
- 不再需要在 cicd 過程中引入其它 devops 用到的設定檔
- 可以獨立 build 和 deploy 的 stage 讓 developer 專注於自己僅需觀察自己 repo 的 build result 而 devops 可以自己管理 deploy flow

缺點   
- 若在 build stage 需要置換 developer 的 configuration file 仍是需要找其他解法
- cicd pipeline 變得較不直觀，且搭配 external-ci 的情況下，會變得更為複雜


## 流程說明
1. 在 source code 的 repo 設定 `parent-ci.yml` 的 flow，裡面的 trigger job 會觸發對應的 project 管道
2. 在 devops 的 repo 設定像 `child-ci.yml `