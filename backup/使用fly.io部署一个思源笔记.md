直接使用官方的 Docker 镜像，做以下几个改动

1. 配置端口映射，将内部端口映射到 443
2. 创建一个存储卷，挂载到 Docker 内部的 workspace 目录

    ```
    fly volume create siyuan_data -r hkg -s 1
    ```

3. 由于官方镜像一定要指定 accesskey 才能启动，所以需要使用到 fly 的 experimental 特性，在 fly.toml 中指定 exec 启动参数，添加 docker 启动的命令行
配置文件如下：

    ```
    app = "app_name"
    primary_region = "hkg"
    
    [experimental]
      cmd = ["--accessAuthCode=xxx"]
    
    [build]
      image = "b3log/siyuan:latest"
    
    [mounts]
      source = "siyuan_data"
      destination = "/home/siyuan/SiYuan"
      processes = ["app"]
    
    [http_service]
      internal_port = 6806
      force_https = true
      auto_stop_machines = true
      auto_start_machines = true
      min_machines_running = 0
      [http_service.concurrency]
        type = "requests"
        hard_limit = 250
        soft_limit = 200
    ```

4. 到这里 deploy 后就可以访问了。
5. 为了数据安全性，启动后配置一个云端存储作为同步和备份，支持 s3, 可以继续薅 cloudflare r2 羊毛


<!-- ##{"timestamp":1698815160}## -->