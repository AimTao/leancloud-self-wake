# leancloud-self-wake

用 Valine 做评论系统，用 LeanCloud 储存数据，并用云引擎部署 web服务管理评论内容，并邮件提醒。

近期 LeanCloud 出现 **“因流控原因，通过定时任务唤醒体验版实例失败，建议升级至标准版云引擎实例避免休眠”**  问题。

本仓库利用 Github Action 执行定时唤醒，防止其大白天休眠。



# USE

1. fork 此仓库
2. 在 setting -> Secrets，添加一个 secret，Name 为 SITE，Value 为 **评论后台网站的地址**。
3. star 自己的仓库，这样是为了手动触发一次定时任务。



# ADDED

图文见blog：[一行命令解决 LeanCloud 流控问题](https://www.aimtao.net/slef-wake-leancloud/)


# UPDATA

提醒：60 天此仓库没有任何更新，Github Action 就会被停止，点击 Action 页面的激活按钮就可以重新启动。


# FREEZE
我已经用 crontab 来替代 Github Action 了，如果你有服务器，只需 `crontab -e` 设置定时任务。
```sh
*/29 7-23 * * * curl https://your_site && date "+%D %H:%M:%S" >> ~/curl_log
```
