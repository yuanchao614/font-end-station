# font-end-station

This site is built with [hexo](http://hexo.io/). Site content is written in Markdown format located in `src`. Pull requests welcome!

## Developing

``` bash
$ npm install
$ npm start # dev server at http://localhost:4000
```

## 修改
```
// 修改更目录下—config.yml文件里面的deploy选项
deploy:
  type: git
  repository: https://github.com/yuanchao614/yuanchao614.github.io.git  // 改成你的GitHub仓库地址，仓库名必须是： 用户名.GitHub.io
  branch: master
```

## 部署
```
hexo g

hexo d
```

