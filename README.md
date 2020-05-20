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
