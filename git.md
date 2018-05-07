# GIT

## FLOW
  - CODE REVIEW
    - <del>`fork`一份代码至自己仓库</del>,开发完一部分功能后将该部分代码以`pull request`的方式提到主仓库，并需要指定`reviewer`
### 分支管理
#### 单迭代
  - 分支类型：
    - `master`： 发布至`stage`环境和`production`环境
    - `dev`：发布至`test`环境
    - `feature/xxx`：开发分支
    - `hotfix/xxx`： 紧急bug修复分支

  - 流程及限制：
    - `feature`分支从`dev`分支进行`fork`
    - 开发阶段，只允许在`feature`分支上进行开发
    - 提测阶段, 第三轮提测后，若有需要紧急修复的bug，可以在`dev`分支上进行开发，其余阶段均只可在`feature`分支上进行开发
    - 提测时，将`feature`分支合并到`dev`分支
    - 完成所有测试后，上`stage`环境之前，将`dev`分支合并至`master`
    - `stage`环境和`production`环境的代码均用`master`分支代码进行发布

#### 多迭代
  - 分支类型：
    - master
    - dev
    - hotfix
    - 迭代1
      - feature/main
      - feature/xxx
      - feature/yyy
    - 迭代2
      - feature/main
      - feature/xxx

  - 流程及限制：
    1. 启动开发时，从`master`拉取一个迭代主分支`feature/main`（迭代的区分可以加前缀）
    2. 开发的功能从`feature/main`拉取不同的`feature`分支
    3. 提测时将所有功能合并到`feature/main`,本地测试没问题后将`feature/main`覆盖到`dev`，发布到机器上
    4. 测试完成后将`dev`合并到`master`，发`stage`环境的机器
    5. `stage`环境没问题的话就发线上机器

  - 其他情况
    1. 两个迭代同时间点上线，协调上线时间，避免同时上线。若无法避免，则需要拉取`stage`分支上`st`环境，`dev`不能直接合并到`master`.
    2. 非提测代码不允许提到`dev`,防止有脏代码。

## COMMIT MESSAGE
  - feat：新功能（feature）
  - fix：修补bug
  - docs：文档（documentation）
  - style： 格式（不影响代码运行的变动）
  - refactor：重构（即不是新增功能，也不是修改bug的代码变动）
  - test：增加测试
  - chore：构建过程或辅助工具的变动
