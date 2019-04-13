### Nginx

```
roles:
    - {
        role: nginx,
        conf_file: test.conf,
        http_port:9081,
        ngx_hosts: "test.abc.com",
        ngx_ports: "8080",
		ssl: true,
		ssl_domain: 'abc.com',
		ssl_port: 443,
        include_conf: test.j2,
        limit: true|false,
        limit_mem: 10,
        limit_req: 5,
        limit_conn: 5,
        limit_burst: 5,
		real_ip: true,
        real_ip_filter: '10.0.0.0/8,127.0.0.1',
        limit_whiteips: '10.0.0.0/8,127.0.0.1',
        cors: true,
        cors_domain: "abc.com",
        action: "unload",
		proxy_protocol:true,
        unload_seconds:5,
        unload: 'test1.abc.com|test1',
    }
```

conf_file: 自定义配置文件，忽略以下配置
ngx_hosts: 配置Host,必需，支持数组和逗号分割string形式
ngx_ports: 配置端口,默认监听8080,非必需，支持单个端口，数组和逗号分割string形式
http_port: Upstream服务器端口
ssl: 开启https
ssl_domain:　加载的证书文件前缀，非必须，默认取nginx_hosts第一个域名
ssl_port: 开启https的端口，默认全部开启，否则只开启该端口的https
include_conf: 自定义Location配置，非必需
limit: 开启IP访问限制,设置限制频率,非必需
limit_mem: limit内存分配大小,单位M,默认10
limit_req: limit并发请求数,单位r/m,默认5
limit_conn: limit并发连接数,默认5
limit_burst: limit缓存连接数,默认5
limit_whiteips: 白名单，不执行limit,120.0.0.1和10.0.0.0/8默认已包括
real_ip: 开启realip模块
real_ip_filter : 过滤真实IP来源
cors: 支持cors头
cors_domain: 自定义cors 域名
proxy_protocol: 打开proxy_protocol模式，获取真实IP需要同时打开realip
action: unload时触发平滑迁移流量,非必需
unload_seconds: unload等待时间,非必需
unload: unload迁移服务器地址,支持单服务器地址和组地址,非必需


### Supervisor
```
roles:
    - {
        role: supervisor,
        program_id: "xxxx",
        command: "xxxx",
        args: "",
        state: restarted,
        envs: "xxx"
    }
```

program_id: 标示
command: 具体运行命令
envs: [map or string]
state: present|started|stopped|restarted|absent
envs: [map or string]
