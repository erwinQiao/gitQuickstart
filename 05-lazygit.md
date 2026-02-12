# Lazygit使用

## lazygit add


假设你修改了文件，并进行`Ctrl`+`S`保存，lazygit会自动检测到你的修改，最好是多改几个文件，多修几行

- 在[2]中File-Worktrees-Submodules中的`File`中，可以看到当前修改的文件是`01-基础教程`，前面有`M`表示正在修改

1. 你可以直接使用`Space`空格键，直接相当于`git add file.txt`文件
2. 你可以使用`a`,表示直接使用`git add ./`，把所有修改的文件都添加到暂存区

- 点击当前的文件，然后按`Enter`回车键，进入文件修改界面
- 就是[0]状态栏中显示的样子(分为Ubstaged changes和Staged Changes)

> @@ -a,b +c,d @@ 表示：
> 旧文件从第 a 行开始的 b 行，被新文件中从第 c 行开始的 d 行替换。


## lazygit commit

在上一步进行修改和`git add`之后，就是进行`git commit`操作了

选中文件之后，按`c`键,会看到commit要求的message提示

- 添加commitxx信息，然后按`Enter`回车键，进行commit操作 相当于`git commit -m "message0"`
- description可以不写，但是最好写上，方便后续的回溯

*如何使用`git commit -amend `？*

Lazygit给了更方便的操作，在[04]工作栏中点击`commit`，然后会出现`Amend commit`提示，点击确定即可追加commit，commit的信息不变，但是commit的hash会发生改变

- 按 4 进入 Commits 面板。(或者点击4的commit即可)
- 选中最顶端的那条提交（也就是你刚刚完成的那条）。
- 按`r`进入修改信息界面。修改之后按`Enter`确认即可


## lazygit branch

分支是git的核心，也是git的精髓

**创建分支**

在文件目录中进入bash，输入`lazygit`，切换到lazygit界面

在[03]的工作区域，点击`Local branch`，最下方会有提示

> checkout<space>; New Branch<n>; delete<d>; Rebase<r>; Reset<g>; Upsteam<u>; Merge<m>; Stash<s>; Rename<Enter>

**切换分支**

- 按`n`进入到创建分支的界面，输入分支的名称，确认`Enter`就可,默认直接切换到`dev`分支，等价于`git switch -c dev`或旧版的命令`git checkout -b dev`

而构建分支之后，如何切换？
- 按`Space(空格)` 是最稳妥的切换和检出(checkout)
- 按`Enter`现在就是展开commit，而不是切换了，需要注意
- 如果进入预览了，按`Esc`或`q` 即可回到左侧的分支选择列表

**合并分支**


在feature(dev改命)分支下，继续创建一个`bugfix`分支，然后修改文件，在创建的瞬间就能看到`commit 9a26c6b`将(HEAD--> bugfix,feature)表示HEAD当前的进度

- bugfix分支修改之后，进行快速操作，就看到`commit a110f7f`(HEAD --> bugfix)，这就是HEAD指向最前端的精髓
- 点击每一个分支都展现出来当前分支的commit 线路

:::{.callout}
非常的直观查看commit历史线，出现冲突之后能快速的找到问题所在--lazygit的强大之处
:::lazy

- 在[03]工作区域，点击`Local branch`，选择`feature`分支，然后按`space`切换分支到`feature`
- 按`M`表示merge分支(下方都有提示，如果忘记了可以查看下方)，会出现多种提示
    - Regular merge(fast - forward) 快进模式 m
    - Regular merge(no fast - forward) 普通模式 带有commit信息 n
    - Squash merge and leave uncommitted s
    - Squash merge and commit s


> 这种就是最直观的表示，你的本地 main 分支，比远程仓库的 origin/main 多了 1 个提交


:::{.callout-note}

遇到冲突解决问题，才是git的核心。比如合并分支的时候发生冲突，一定要找到冲突的来源，否则就是一直很混乱

:::

- 合并的`feature`和`main`的过程中发生冲突
- 在[02]Files中直接提醒冲突`UU 05-lazygit.md`

在冲突视图中

| 快捷键 | 作用                 |
| `e` | 手动编辑               |

解决了冲突，继续合并即可,按`P`进行推送


