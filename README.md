# chrome-web
远程浏览器

GitHub Codespaces 版（拿美国出口 IP）

.devcontainer/devcontainer.json：

```json
{
  "name": "us-chrome",
  "image": "lscr.io/linuxserver/chromium",
  "runArgs": ["--shm-size=1gb"],
  "containerEnv": {
    "PUID": "1000",
    "PGID": "1000",
    "TITLE": "Chrome"
  },
  "forwardPorts": [3000],
  "portsAttributes": {
    "3000": {
      "label": "Chrome",
      "onAutoForward": "openBrowser"
    }
  }
}
```

# 关键步骤——指定美国区域：  

仓库页面点 Code → Codespaces 标签页右边的 "..."（三个点）→ New with options...  
在弹出的 Region 下拉框里选 US East 或 US West（不选的话默认走离你最近的区域，可能不是美国）  
点击 Create，等容器起来  
到 Ports 标签把端口 3000 的 Visibility 改成 Public  
点开转发链接，就是全屏 Chrome，出口 IP 是美国  

# 备注
想加访问密码：加 -e CUSTOM_USER=xxx -e PASSWORD=xxx 两个环境变量（Codespaces 里对应写进 containerEnv）。  
这个镜像默认是 root 权限、无沙箱模式，仅个人临时用没问题，别长期暴露公网。  
Codespaces 免费额度每月 120 core-hours，2 核机型约 60 小时，用完记得 Stop，不然会计费或额度耗尽。  
