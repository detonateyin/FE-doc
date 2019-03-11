# Git之小技巧

### 1. Pull Request

> Pull Request本质是一种对话机制，你可以在提交的时候，@相关人员或团队，引起他们的注意。

### 2. Protected branch

> master分支应该受到保护，不是每个人都可以修改这个分支，以及拥有审批 Pull Request 的权力。

### 3. Issue

>Issue 用于 Bug追踪和需求管理。建议先新建 Issue，再新建对应的功能分支。功能分支总是为了解决一个或多个 Issue。

>功能分支的名称，可以与issue的名字保持一致，并且以issue的编号起首，比如"15-require-a-password-to-change-it"。

>开发完成后，在提交说明里面，可以写上"fixes #14"或者"closes #67"。Github规定，只要commit message里面有下面这些动词 + 编号，就会关闭对应的issue。

>- close
>- closes
>- closed
>- fix
>- fixes
>- fixed
>- resolve
>- resolves
>- resolved

> 这种方式还可以一次关闭多个issue，或者关闭其他代码库的issue，格式是username/repository#issue_number。

>Pull Request被接受以后，issue关闭，原始分支就应该删除。如果以后该issue重新打开，新分支可以复用原来的名字。

### 4. Merge节点

### 5. Squash 多个commit
>为了便于他人阅读你的提交，也便于cherry-pick或撤销代码变化，在发起Pull Request之前，应该把多个commit合并成一个。（前提是，该分支只有你一个人开发，且没有跟master合并过。）
>这可以采用rebase命令附带的squash操作

关于rebase
>当需要保留详细的合并信息的时候建议使用git merge，特别是需要将分支合并进入master分支时；当发现自己修改某个功能时，频繁进行了git commit提交时，发现其实过多的提交信息没有必要时，可以尝试git rebase。

可以参考[《Git merge和rebase分支合并命令的区别》](https://juejin.im/post/5af26c4d5188256728605809)

## 附录一：参考链接
1. [Git 工作流程](http://www.ruanyifeng.com/blog/2015/12/git-workflow.html)