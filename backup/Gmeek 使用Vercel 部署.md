

Github Pages 要求必须使用公开仓库，如果要使用私有仓库，可以使用vercel部署。

> [!NOTE]
> 使用本文的部署方式，因为私仓的原因存在两个问题：
> 1. Issue中上传的图片，无法正常显示（可以通过图床解决，但脱离了Gmeek简单的初衷）。
> 2. 评论功能无法正常使用。

1. 在vercel上导入Gmeek项目
2. 在vercel上修改网页静态文件路径为docs
![image](https://github.com/FFute/gmeek/assets/8198810/13e8215a-9f2f-42fe-a168-9f9c48abad18)
3. 修改Github Action, 去除对Pages的依赖操作
![image](https://github.com/FFute/gmeek/assets/8198810/cead0e18-895c-4378-bdd1-3c020941e34a)
![image](https://github.com/FFute/gmeek/assets/8198810/ea415c69-509b-4762-ace4-3048cb00dbe5)

操作完成后就可以把仓库转为私有，通过vercel部署和访问了。
正常写issue后，vercel也会自动发布更新。