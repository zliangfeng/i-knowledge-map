# mac-homebrew-tips


## 清理不常用的包

- brew 安装的包有点多，又不知道那些能删除
  - 先用`brew deps --tree --installed` 展示一下依存关系，
  - `brew uninstall formula`
  - `brew autoremove` 删除依赖项
