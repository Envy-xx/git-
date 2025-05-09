# Git 常用操作速查表 🚀

本速查表汇总了日常开发中常用的 Git 命令，希望能帮助你更高效地使用 Git。

## ✨ 初始化与配置 (Setup & Config)

| 命令                                       | 描述                              |
| :----------------------------------------- | :-------------------------------- |
| `git init`                                 | 在当前目录初始化一个新的 Git 仓库 |
| `git clone [url]`                          | 克隆一个远程仓库到本地            |
| `git config --global user.name "[name]"`   | 设置全局提交者名称                |
| `git config --global user.email "[email]"` | 设置全局提交者邮箱                |
| `git config --list`                        | 查看所有 Git 配置                 |
| `git config --global --edit`               | 编辑全局配置文件                  |

## 📝 工作区与暂存区 (Working & Staging)

| 命令                           | 描述                                                     |
| :----------------------------- | :------------------------------------------------------- |
| `git status`                   | 查看工作区和暂存区的状态                                 |
| `git add [file]`               | 将指定文件添加到暂存区                                   |
| `git add .`                    | 将当前目录下所有已修改和新添加的文件添加到暂存区         |
| `git add -A`                   | 将所有已修改、新添加和已删除的文件添加到暂存区           |
| `git reset [file]`             | 将指定文件从暂存区移除，但保留工作区的修改               |
| `git checkout -- [file]`       | 撤销工作区中对指定文件的修改（慎用，会丢失未保存的更改） |
| `git rm [file]`                | 从工作区和暂存区删除文件                                 |
| `git rm --cached [file]`       | 从暂存区删除文件，但保留在工作区                         |
| `git mv [old-name] [new-name]` | 重命名文件，并将更改加入暂存区                           |

## 💾 提交与历史 (Committing & History)

| 命令                                         | 描述                                                        |
| :------------------------------------------- | :---------------------------------------------------------- |
| `git commit -m "[message]"`                  | 将暂存区的内容提交到本地仓库，并附带提交信息                |
| `git commit -am "[message]"`                 | 将所有已跟踪文件的修改加入暂存区并一同提交 (跳过 `git add`) |
| `git commit --amend`                         | 修改最后一次提交（会覆盖上一次提交，不要用于已推送的提交）  |
| `git log`                                    | 查看提交历史                                                |
| `git log --oneline`                          | 单行显示提交历史                                            |
| `git log --graph --decorate --all --oneline` | 图形化展示所有分支的简洁提交历史                            |
| `git log -p -[n]`                            | 显示最近 n 次提交的详细差异                                 |
| `git show [commit-hash]`                     | 显示某次提交的详细信息和更改内容                            |
| `git diff`                                   | 查看工作区与暂存区的差异                                    |
| `git diff --staged` (或 `git diff --cached`) | 查看暂存区与上一次提交的差异                                |
| `git diff [commit1] [commit2]`               | 查看两次提交之间的差异                                      |

## 🌿 分支管理 (Branching)

| 命令                                  | 描述                                                    |
| :------------------------------------ | :------------------------------------------------------ |
| `git branch`                          | 列出所有本地分支 (当前分支会用 `*` 标记)                |
| `git branch -a`                       | 列出所有本地分支和远程跟踪分支                          |
| `git branch [branch-name]`            | 创建一个新分支                                          |
| `git checkout [branch-name]`          | 切换到指定分支 (Git 2.23+ 推荐 `git switch`)            |
| `git switch [branch-name]`            | (新) 切换到指定分支                                     |
| `git checkout -b [branch-name]`       | 创建并立即切换到新分支 (Git 2.23+ 推荐 `git switch -c`) |
| `git switch -c [branch-name]`         | (新) 创建并立即切换到新分支                             |
| `git branch -m [old-name] [new-name]` | 重命名本地分支                                          |
| `git merge [branch-name]`             | 将指定分支合并到当前分支                                |
| `git rebase [branch-name]`            | 将当前分支的提交变基到指定分支之上                      |
| `git branch -d [branch-name]`         | 删除已合并的本地分支                                    |
| `git branch -D [branch-name]`         | 强制删除本地分支（即使未合并）                          |

## 🔄 远程操作 (Remotes)

| 命令                                            | 描述                                                         |
| :---------------------------------------------- | :----------------------------------------------------------- |
| `git remote -v`                                 | 查看已配置的远程仓库                                         |
| `git remote add [name] [url]`                   | 添加一个新的远程仓库                                         |
| `git remote remove [name]`                      | 移除指定的远程仓库                                           |
| `git remote rename [old-name] [new-name]`       | 重命名远程仓库                                               |
| `git fetch [remote-name]`                       | 从远程仓库下载最新的提交历史和对象，但不自动合并             |
| `git pull [remote-name] [branch-name]`          | 拉取远程仓库的指定分支并与当前本地分支合并 (`Workspace` + `merge`) |
| `git push [remote-name] [branch-name]`          | 将本地指定分支的提交推送到远程仓库                           |
| `git push -u [remote-name] [branch-name]`       | 推送并设置上游分支（后续可直接 `git push` / `git pull`）     |
| `git push [remote-name] --delete [branch-name]` | 删除远程仓库的指定分支                                       |
| `git push [remote-name] :[branch-name]`         | (同上) 删除远程分支的另一种语法                              |
| `git push --tags`                               | 推送所有本地标签到远程仓库                                   |

## ↩️ 撤销与重置 (Undoing & Resetting)

| 命令                                               | 描述                                                         |
| :------------------------------------------------- | :----------------------------------------------------------- |
| `git reset HEAD [file]`                            | (同 `git reset [file]`) 将文件从暂存区取消暂存               |
| `git reset --soft HEAD~1`                          | 撤销最后一次提交，保留更改在暂存区                           |
| `git reset HEAD~1` (或 `git reset --mixed HEAD~1`) | 撤销最后一次提交，保留更改在工作区（默认模式）               |
| `git reset --hard HEAD~1`                          | **[危险]** 撤销最后一次提交，并丢弃所有相关的更改            |
| `git reset --hard [commit-hash]`                   | **[危险]** 回滚到指定的提交，丢弃该提交之后的所有更改        |
| `git revert [commit-hash]`                         | 创建一个新的提交来撤销指定提交的更改（更安全，保留历史）     |
| `git clean -fd`                                    | **[危险]** 清除工作区中未跟踪的文件和目录（`-n` 预览，`-f` 强制，`-d` 包含目录） |

## 📦 储藏 (Stashing)

| 命令                         | 描述                                      |
| :--------------------------- | :---------------------------------------- |
| `git stash`                  | 将当前工作区的修改（已跟踪文件）储藏起来  |
| `git stash save "[message]"` | 带消息储藏                                |
| `git stash list`             | 查看所有储藏                              |
| `git stash pop`              | 应用最近的储藏并从储藏列表中移除          |
| `git stash apply stash@{n}`  | 应用指定的储藏 (如 `stash@{0}`), 但不移除 |
| `git stash drop stash@{n}`   | 移除指定的储藏                            |
| `git stash clear`            | **[危险]** 清除所有储藏                   |

## 🏷️ 标签 (Tagging)

| 命令                                         | 描述                                    |
| :------------------------------------------- | :-------------------------------------- |
| `git tag`                                    | 列出所有标签                            |
| `git tag [tag-name]`                         | 创建一个轻量标签 (指向当前提交)         |
| `git tag -a [tag-name] -m "[message]"`       | 创建一个附注标签 (包含作者、日期、信息) |
| `git tag -d [tag-name]`                      | 删除本地标签                            |
| `git push [remote-name] [tag-name]`          | 推送指定标签到远程仓库                  |
| `git push [remote-name] --tags`              | 推送所有本地标签到远程仓库              |
| `git push [remote-name] --delete [tag-name]` | 删除远程标签                            |

---

希望这个速查表对您有所帮助！😊