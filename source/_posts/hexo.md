# hexo + github

+ 1
```
建立空仓库
git clone git@github.com:ghxdghxd/ghxdghxd.github.io.git
cd ghxdghxd.github.io
建立分支并切换
git checkout hexo
```
+ 2
```
初始化hexo
mkdir Blog
npm install hexo
hexo init
npm install
cp -a Blog/* ghxdghxd.github.io
rm -r Blog
mv ghxdghxd.github.io Blog
cd Blog
npm install hexo-deployer-git
```

+ 3
```
修改_config.yml, 用git可以免密码，如用https:则不免密码
deploy:
  type: git
  repository: git@github.com:ghxdghxd/ghxdghxd.github.io.git
```