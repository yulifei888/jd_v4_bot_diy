# jd_v4_bot_diy
本仓库只是对Annyoo2021大佬jd_v4_bot（ https://github.com/Annyoo2021/jd_v4_bot.git ）的diy，特此感谢，如有侵权，请联系我删除，转发请注明出处。

1. jup.sh添加 https://ghproxy.com/ 前缀，对国内网络更友好
2. v4mb.sh添加 https://ghproxy.com/ 前缀，对国内网络更友好

# 使用方法
1. 原教程第4、安装面板命令改为：
```
wget -q https://ghproxy.com/https://raw.githubusercontent.com/feng1168/jd_v4_bot_diy/main/v4mb.sh -O v4mb.sh && chmod +x v4mb.sh && ./v4mb.sh
```
2. 打开网页控制面板，“自定义脚本”底部添加如下代码并保存，“首页配置”中EnableJupDiyShell的值改为true
```
echo -e "====================== 加载feng1168的diy ======================\n"
ping -W1 -c1 https://ghproxy.com/https://raw.githubusercontent.com >/dev/null 2>&1
if [ $? = 0 ]; then
  echo -e "正在加载...\n"
  rm -f jup.sh
  wget -q https://ghproxy.com/https://raw.githubusercontent.com/feng1168/jd_v4_bot_diy/main/jup.sh -O jup.sh && chmod +x jup.sh
  echo -e "加载完成\n"
else
  echo -e "无法下载，请检查网络\n"
fi
```
