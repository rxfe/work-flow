# GIT

## FLOW
  - CODE REVIEW
    - `fork`一份代码至自己仓库, 开发完一部分功能后将该部分代码以`pull request`的方式提到主仓库，并需要指定`reviewer`
  - 分支管理
    - 类型：
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

## COMMIT MESSAGE
  - feat：新功能（feature）
  - fix：修补bug
  - docs：文档（documentation）
  - style： 格式（不影响代码运行的变动）
  - refactor：重构（即不是新增功能，也不是修改bug的代码变动）
  - test：增加测试
  - chore：构建过程或辅助工具的变动
