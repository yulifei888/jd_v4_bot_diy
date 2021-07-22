# jd_v4_bot_diy
本仓库只是对Annyoo2021大佬jd_v4_bot（ https://github.com/Annyoo2021/jd_v4_bot.git ）的diy，特此感谢，如有侵权，请联系我删除，转发请注明出处。

1. jup.sh添加 https://ghproxy.com/ 前缀，对国内网络更友好
2. v4mb.sh添加 https://ghproxy.com/ 前缀，对国内网络更友好
3. 可选：开启财富岛热气球挂机

# 使用方法
1. 原教程第4、安装面板命令改为：
```
wget -q https://ghproxy.com/https://raw.githubusercontent.com/feng1168/jd_v4_bot_diy/main/v4mb.sh -O v4mb.sh && chmod +x v4mb.sh && ./v4mb.sh
```
2. diy.sh底部添加下面的代码，config.sh中EnableJupDiyShell的值改为true；可选：开启财富岛热气球挂机，diy.sh顶部的export ENABLE_HANGUP的值改为true
```
echo -e "======================== 加载feng1168的diy ========================\n"
echo -e "正在加载...\n"
rm -f jtask.sh
wget -q https://ghproxy.com/https://raw.githubusercontent.com/feng1168/jd_v4_bot_diy/main/jtask.sh -O jtask.sh && chmod +x jtask.sh
rm -f jup.sh
wget -q https://ghproxy.com/https://raw.githubusercontent.com/feng1168/jd_v4_bot_diy/main/jup.sh -O jup.sh && chmod +x jup.sh
echo -e "加载完成\n"

if [[ $ENABLE_HANGUP == true ]]; then
   echo -e "======================== 启动挂机程序 ========================\n"
   pm2 id jd_cfd_loop
   hangup_check_results=$(pm2 id jd_cfd_loop)
   if [[ $hangup_check_results == "[]" ]]; then
       . $JD_DIR/config/config.sh
       if [[ $Cookie1 ]]; then
           jtask hangup 2>/dev/null
           echo -e "挂机程序启动成功...\n"
       else
           echo -e "config.sh中还未填入有效的Cookie，可能是首次部署容器，因此不启动挂机程序...\n"
       fi
   else
   echo -e "挂机程序已经启动了.\n"
   fi
elif [[ ${ENABLE_HANGUP} == false ]]; then
    echo -e "已设置为不自动启动挂机程序，跳过...\n"
fi
```
