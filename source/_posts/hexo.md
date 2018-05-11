---
title: hexo安装配置
---
+ 1

```bash
建立空仓库
git clone git@github.com:ghxdghxd/ghxdghxd.github.io.git
cd ghxdghxd.github.io
建立分支并切换
git checkout hexo
```

+ 2

```bash
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

```bash
修改_config.yml, 用git可以免密码，如用https:则不免密码
deploy:
  type: git
  repository: git@github.com:ghxdghxd/ghxdghxd.github.io.git
```

+ 4 pdf插件

```bash
直接插入并显示pdf
npm install hexo-pdf
{% pdf /images/name.pdf %}
```

+ 5 插入脚注(reference)

```bash
npm install hexo-reference --save
例：
basic footnote[^1]
here is an inline footnote[^2](inline footnote)
and another one[^3]
and another one[^4]

[^1]: basic footnote content
[^3]: paragraph
footnote
content
[^4]: footnote content with some [markdown](https://en.wikipedia.org/wiki/Markdown)
```