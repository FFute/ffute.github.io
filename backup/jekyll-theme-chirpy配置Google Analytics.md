jekyll-theme-chirpy 主题本身已经内置了Google Analytics插件，使用时候只需在`_config.yml`中修改如下配置

```yaml
google_analytics:
  id: 'G-XXX' # fill in your Google Analytics ID
```

其中G-XXX替换为你自己的Google track id

但是实际部署后发现配置不生效，主题本身的文档中对这一块的说明也缺失。

下载主题源代码后，查看发现还有另外一个开关配置  
`jekyll.environment == 'production'`

```liquid
{if jekyll.environment == 'production' and site.google_analytics.id != empty and site.google_analytics.id }
   ...
{ endif }
```

参考Jekyll[官方文档](https://jekyllrb.com/docs/configuration/environments/) , 这个配置只在生产站点生效。
> When you build your Jekyll site, the content inside the `if` statement won’t be run unless you also specify a `production` environment in the build command, like this:  
> ```bash
> JEKYLL_ENV=production jekyll build
> ```
> The default value for `JEKYLL_ENV` is `development`. Therefore if you omit JEKYLL_ENV from the build arguments, the default value will be `JEKYLL_ENV=development`.

默认是development所以不会生效，所以我们需要在生成网站时指定环境变量。

如果你和我一样使用Vercel进行网站托管，可以在Vercel的站点设置中简单的给product环境添加环境变量JEKYLL_ENV=product。

![](https://raw.githubusercontent.com/FFute/img/main/picgo/202311151419072.png)

<!-- ##{"timestamp":1700017560}## -->
