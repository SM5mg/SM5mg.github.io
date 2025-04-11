---
title: GitHub基本操作|VSCode关联GitHub
tags:
  - Github
categories:
  - 技术乱炖
  - 技术分享
abbrlink: 7375d15a
---
学习记录及分享

<!-- more -->

## 一.Git 基础知识

### **1. Git**

Git 是一个开源的分布式版本控制系统，由 Linus Torvalds 于 2005 年创建，用于有效地跟踪和管理源代码历史。它允许多人协作，同时保持代码历史的完整性和一致性。Git 的核心概念包括提交（commit）、分支（branch）、合并（merge）和冲突解决（conflict resolution）。

### **2. GitHub**

GitHub 是一个基于 Web 的平台，提供 Git 仓库的托管服务，并增加了协作功能。它使得代码共享、协作和版本控制更加容易，特别是在团队项目中。GitHub 的特色功能包括 Pull Requests、Issues、GitHub Actions 等。

### **3. Git 与 GitHub 的关系**

**Git 是版本控制系统的核心，而 GitHub 是在此基础上构建的服务平台。**

**Git 是版本控制工具，相当于存档记录器**。可以在电脑不联网的情况下，在本地电脑直接使用。它可以更好的帮助你管理程序，记录提交的历史内容，历史更改记录，当你误删误操作时，及时修复还原。

**GitHub 是代码托管网站，且具有协作和社交网络的功能**。每个程序员都可以将自己写的程序代码托管到 Github 的仓库中，这个仓库可以公开（也称开源）也可以保密。如果公开，所有人都能看到你的代码，他们可以看到你的提交记录，也可以参与到你的代码修改工作中，同你共同完成代码的编写。

### **4.Git 和 GitHub 的工作流**

**Git 工作流程**

> 几个概念：
> 本地库 Origin：个人终端上的代码文件；
> 工作区 Changes：个人终端上修改代码的工作区；
> 暂存区 Stage Changes：临时代码中转站，待定区；
> 远程库 Remote：存储在 Github 仓库中的代码文件；

{% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228110148.png %}



✅**完整流程**✅
➡️**新项目初始化**：项目初次使用需要建立新的文件夹，并使用 `git init` 初始化。这会在本地工作区生成一个.git 文件夹。里面存放着是本地库相关的子目录和文件，不要删除，也不要胡乱修改。
➡️**增删改写**：在本地库工作，对代码进行增删改等任意操作，此时只要不提交到暂存区都属于【**工作区**】状态，文件属于未跟踪`Untracked`状态。
➡️**添加版本更改记录**：代码完成后，使用`git add`将文件从【**工作区**】添加到【**暂存区**】临时存储，文件从`Untracked`状态变为`Added`状态。
➡️**提交更改**：确认暂存区的文档没问题后，使用`git commit`将【**暂存区**】的更改记录存储到【**本地库**】数据库进行记录。
➡️**新建远程库**：新项目需要先在`github`中新建仓库，这个仓库将来用于存放本地库的内容。
➡️**连接远程库**：远程库新建好后，使用`git remote`进行连接。
➡️**推送更改**：本地库的代码确认无误后，使用`git push`将【**本地库**】最终更改上传到【**远程库**】，让更多人看到你的代码更新。
➡️**拉取更改**：如果其他人在【远程库】上传了更改，可以在【**本地库**】使用`git pull`从【**远程库**】获取最新更改。
➡️**克隆仓库**：如果想获取他人的项目，可以使用`git clone`复制【**远程库**】到【**本地库**】。

**GitHub 工作流程**

➡️**创建仓库**：在 GitHub 上创建新仓库用于项目。
➡️**分支管理**：使用分支 Fork 进行特定任务的开发。
➡️**合并请求**：通过 Pull Requests 进行代码审查和合并 merge。
➡️**Issues 跟踪**：使用 Issues 跟踪任务、增强功能和错误。

## 二.VSCode 使用 Git 版本控制

**开始之前，请注意以下几点：**

- 请确保已安装最新的 VS Code。[Visual Studio Code](https://code.visualstudio.com/)
- 请确保已安装最新版的 Git。[https://git-scm.com/download](https://git-scm.com/download) ，并将 git 新增到环境变量中，确保任意路径可以访问。
  VSCode 集成了 Git 功能且支持基本的 git 命令，使我们能够在开发过程直接提交和获取代码。

**几个名词备注：**

U：Untracked 未追踪
A：Added 已添加
M：Modified 已更改
Changes:工作区
Staged Changes:暂存区

### 案例 1.本地库上传远程库

本地电脑任意位置新建文件夹。我这里新建到桌面，命名 Github-test。进入文件夹，右键打开 git bash.
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/eb5158e044169d110de4080610ad78b.png %}

1. git init 初始化文件夹 `Github_test`.
   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/81f94f92bfd2ac7bb883e7bedd196f8.png %}

2. 文件夹 Github_test 中新建 2 个 txt 文件用于测试：hello-1.txt,hello-2.txt,并在 2 个 txt 文档中随意写个单词。

3. 打开 vscode,并用 vscode 打开此文件夹。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/1f47ae670fc831e89ea0f16dafac3e2.png %}

4. 最左侧第三个按钮，有蓝色弹窗 2.点开，这里就是 git 的工作区。U 表示两个文件 untracked 未追踪（仅有修改痕迹但是未上传暂存区）.
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/b03d62a561721ed2e73a8fb58183827.png %}

5. 点击文件旁边的+加号按钮，相当于执行 git add 指令，将文件上传到暂存区 Stage changes。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/1391f7011039cd4e000fba608fe9d8a.png %}

6. 如果想撤销已上传的暂存区文件，可以点击-减号按钮，文件则恢复到工作区(A 变 U)，相当于指令 git reset -- 1.txt。如果想更进一步恢复到工作区更改前，可以使用`git checkout -- hello-1.txt`指令。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/059d0cdeb7d7fd4d6ba1563e879630b.png %}

7. 给暂存区的文件备注'第一次修改'并点击 commit 提交到本地库。相当于执行`git commit -m   '第一次修改' `指令。点击后，工作区文件清空，表示工作已完成，暂无修改记录。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228162629.png %}

8. 再次对 2 个 txt 文件进行修改。进入到文件中，给 hello-1 和 hello-2 新增一个单词，此时左侧第三个按钮再次弹窗，但是状态是 M（已修改）。我们需要将修改后的代码继续重复`git add`提交暂存区和`git commit`提交更改到本地库的动作，对文件更改进行保存。点击加号，新增备注并点击 commit 即可。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/153077690ec7de4e21f5d779164a57f.png %}

9. 假设 git commit 提交备注后，我们想要撤回本次操作到`git add`之前。只需点击三个点，选择`commit-undo last commit`，相当于指令`git reset --soft HEAD~1`。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/5f2e884e4459044812d6b6ba498c03d.png %}

10. 以上操作都可以手动点击操作，也可以使用`ctrl+` `的快捷键打开 vscode 终端进行操作。终端中可以输入任意 git 指令，git status 可查看目前文件状态，git log 可查看历史操作日志。
    {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/63de926da5a265c8a87075a668c7d9e.png %}

11. 文件存储在本地库后还不够，我们需要上传到 github 远程库。此时先在 github 新建仓库（用于存储本地库的文件），再从本地上传。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/d58a7faf7fc1644927e2fd17a88d1f5.png %}
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/a8e384b0512dcb16f829978f6d8d9fd.png %}
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/0ee8b9eaba3c78cca89c5ae02e313c0.png %}

    复制红框中第一行代码，在 vscode 终端执行。

12. 连接远程库并上传文件。`git remote add origin '远程地址'`；`git push -u origin master`;

    {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/ca698aead29af92cfc5ab9703859be9.png %}

    此时，远程的 github 库已经拥有本地的文件。

    13. 最后，如果你想直接下载 github 远程库中别人已经写好的代码。本地 Git 使用指令 git clone '仓库地址' 或直接在 github 点击下载。

        {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228165225.png %}

### 案例 2.多人跨平台处理冲突

使用 git 的时候，经常会遇到冲突；冲突大概率出现于你和其他人同时下载了相同版本的代码在本地库进行修改的场景，如果其他人比你改的快，且在你之前上传到远程库，此时如果你上传更改就会产生冲突，因为你的版本已经不是最新版的远程库（本地库并不会更新你下载后的远程库的更新）。所以大家在提交代码前，一定要先 pull**拉取远程库的代码**，保证自己本地库目前是最新进度，不然就会造成冲突。

在本地电脑 clone 两个远程库的文件，分别命名 A 和 B，并对 AB 进行修改上传到远程库，A 先更新代码，B 随后上传，我们来看看冲突发生现场。{% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228185056.png %}

1. vscode 打开新克隆的文件夹。分别对 AB 的 hello-1.txt 修改，先上传 A 的修改到远程库，使用 git add/git commit/git push 将文件上传。(见上文)

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228185325.png %}

2. A 上传后，再上传 B，看看会发生什么。使用 git add/git commit/git push 上传到远程。

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228190148.png %}

3. 可以看到 vscode 报错，并返回错误的位置。其中 AceptCurrent Change，是保留你的版本；AcceptIncomingChange 是接收其他人的版本；如果你都想要，可以选择 AcceptBothChanges 然后手动修改。

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228190609.png %}

4. 对冲突进行修改，然后再次 git add/git commit/git push 查看。

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228191814.png %}

5. 来到 github 查看 push 情况。可以看到修改的流程是 A 先改，B 随后，B 二次修改。

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228191946.png %}
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228192026.png %}            

所以为了避免这种情况，我们平时再提交和编写代码前，需要多使用 pull 来拉取远程的最新代码。

### 案例 3.处理分支

案例二的情况导致的结果是，不同的人同时处理相同文件时，很容易产生冲突。所以 branch 应运而生。

1. 本地新建文件夹 github-test3,初始化 git init，新增文件 hello-3.txt，使用 git add/git commit 将文件存到本地库等待上传远程库;

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228192643.png          %}

2. 远程新建仓库 test3; git remote 本地连接远程；git push 将本地文件上传到远程。

3. vscode 新建分支起名 new-b.此时已经切换到 new-b 分支，也可以使用指令`git checkout -b  new-b`来切换。

   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228193814.png %}

4. git branch 可以查看本地分支；git branch -a 可以查看本地和远程分支。
   {% image  https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20231228194107.png %}

5. 本地库新建一个文件 hello-4.txt，然后上传分支 new-b。
6. master 分支和 new-b 分支都有文件的修改。此时需要 merge.pull request.rebase 的作用，把你的分支，接到主分支后面。先 pull 一次再 rebase.再 push.push 的时候出错。因为你的版本会覆盖历史的版本，强制 push 可以使用 git push -f，不建议在项目用，自己的文件可以。push 后再 merge.

--没写完，待补充.
