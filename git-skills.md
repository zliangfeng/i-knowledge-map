# git skills

## refs

- <https://www.honeybadger.io/blog/git-tricks/>

## content

### squash merge

- `git squash merge` keep version control history clean and readable
- `git commit --allow-empty -m 'it works!'` blank commits to kick off workflow

### subtree

- `git subtree add -P some/dir --squash http://url/some-repo.git remoteBranch` 将项目中的某个子目录分离出来提交到新的 repo；

- `add/push/pull` 添加/推送/拉去（类比 git 常规操作）

- `git subtree split -P some/dir -b newBranch` 分离到新分支，可以将新分支提交到指定 repo

### useful commons

- [x] `git checkout -b new_branch` 新建branch
