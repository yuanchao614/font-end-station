﻿# font-end-station

This site is built with [hexo](http://hexo.io/). Site content is written in Markdown format located in `src`. Pull requests welcome!

## Developing

``` bash
$ npm install
$ npm start # dev server at http://localhost:4000
```

## 修改
```
deploy:
  type: git
  repository: https://github.com/yuanchao614/yuanchao614.github.io.git  // 改成你的GitHub仓库地址
  branch: master
```

## 部署
```
hexo g

hexo d
```

