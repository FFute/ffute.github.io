由于众所周知的原因，中国大陆用户访问chirpy主题博客时会存在js和css等资源加载慢的问题。

查阅官方文档后，在不修改主题框架的情况下，可以通过配置进行优化，有两个方式：

>Customing Static Assets
Static assets configuration was introduced in version 5.1.0. The CDN of the static assets is defined by file _data/origin/cors.yml, and you can replace some of them according to the network conditions in the region where your website is published.  
Also, if you’d like to self-host the static assets, please refer to the chirpy-static-assets.

1. 修改加载CORS的CDN地址

    默认情况下，原主题默认使用的是jsdelivr的cdn进行js和css加速缓存，但是这个在国内不好用。
    
    相关配置在源代码的 `_data/origin/cors.yml ` 文件中，找到相应的库文件地址，替换为国内的CDN地址即可。以jquery为例：
    
    ```diff
    jquery:
    - js: https://fastly.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.min.js
    + js: https://cdn.staticfile.org/jquery/3.7.1/jquery.min.js
    ```
2. self-host部署
    主题作者也提供了配置为self-host对应的的[asset库](https://github.com/cotes2020/chirpy-static-assets)和相应的配置方法。  
    如果你本身是利用CDN来部署你的博客，而且你的CDN提供商访问速度不错的话，推荐使用这种方式。
    
    修改 `_config.yml` 把self_host修改为 *true*:
    
      ```yml
      # _config.yml
      assets:
        self_host:
          enabled: true
      ```
    
    然后修改github的action配置 `.github/workflows/pages-deploy.yml`，把submodules打开 :
    
      ```diff
      steps:
        - name: Checkout
          uses: actions/checkout@v2
          with:
      +     submodules: true
      ```


完成！


因为有一个库文件在国内cdn没有同步，我现在偷懒使用self_host的方式部署，使用这种方式并且配合vercel部署，基本可以秒开了，速度目前基本满足要求。

<!-- ##{"timestamp":1699684500}## -->