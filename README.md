#项目管理规范建议

#### 中文书写排版

可参考[中文文案排版指北](https://github.com/sparanoid/chinese-copywriting-guidelines)以及 LeanCloud 的[文案风格指南](http://open.leancloud.cn/copywriting-style-guide.html)

## Git

### 分支建议

可主要分为 5 类分支：

* `master`

  开发分支。可用在内测发布

* `pre-production`

  预发布分支。可用作实验室内部公测发布
	
* `productioin`

  发布分支。用于项目正式提交发布

* `feature`

  命名为 `feature/{a-feature}`，用于特性添加。(`{...}`内为替换内容)

* `fix`

  命名为 `fix/{a-bug}`，用于 bug 修复
  
  ### 工作流程
  
  Issue：

1. 在 `issue` 中新建描述，`fix` 对应 `bug` 标签，`feature` 对应 `feature` 标签
2. 指派给自己或他人 A
3. 指定 `issue` 的 `Milestone`
4. A 创建对应分支并推送到远程 git
5. A 在相关 `issue` 中添加 `WIP` 标签（WIP: work in progress，考虑到一些指派后但可能没有在进行中的 `issue`)

Git:

1. 在任务分支（`feature/..` 或 `fix/..`）完成工作后，提交 Pull Request 到 `master` 分支。频率最高
2. `master` PR 合并后，认为可以作为项目预发布版本时，提交 PR 到 `pre-production` 分支。可能一天至多一次
3. `pre-production` PR 合并后，认为可以作为线上正式版本提交时，提交 PR 到 `production` 分支。

PR 提交时，要保证合并无冲突，合并后无错误。需要在提交之前开发自己保证。


### Commit Message

#### 使用中文

使用英文的习惯来自命令行以及 github 许多 `commit` 命令是英文触发。不过更多时候是懒得写那么多字以及习惯一个功能多次 `commit`，这个习惯不好...

且项目是实验室项目，以后应该也不会有老外看，所以我们自己人都约定用中文吧。这样表达能力会强一点...

####  `commit` 信息要有标题和正文

书写统一使用 `Markdown` 格式。

标题限制 50 字以内，内容为总结性文字结尾不加标点，如果有英文则首字母大写且使用祈使语气（不要用过去时!!!）。

标题是必须的，正文可选。更新日志只抓取标题。

详细的更改写在正文里，简要解释 why vs. how 。

## PR & Code Review

当一个分支完成了当前的任务后

1. 提交 PR
2. 描述此次完成的工作，附上 `issue` 链接以在 PR 合并后关闭相关 `issue`
3. 完成 PR 后，回复可合并，约定回复 👍
4. 根据反馈修改代码并提交
5. 收到可合并回复后即可合并
6. 合并代码到 `master` 分支

Github 用于：

* 开发人员沟通

  仅涉及代码实现，并不再允许当前项目开发组之外的人创建 `issue`

* 分支与 `issue` 管理

  一个分支对应一个或多个 `issue`，在该分支合并到 `master` 后，关闭对应的 `issue`

* 代码 release

  在对外的一个版本发布时，创建 release tag
