# NetEase_Music_daily
网易云音乐每日签到与刷歌单，为兼容SCF改自[此项目](https://github.com/t00t00-crypto/wyy-action)<br>
##使用方法<br>
本地环境运行<br>
1.测试环境为python3.7.6,自行安装python3<br>
2.requirements.txt 是所需第三方模块，执行 `pip install -r requirements.txt` 安装模块<br>
3.可在脚本内直接填写账号密码<br>
4.Python 和需要模块都装好了直接在目录 cmd 运行所要运行的脚本。<br>
<br>
Github Actions版本<br>
1.点击项目右上角的Fork，Fork此项目<br>
2.到自己Fork的项目点击Setting→Secrets→New secrets<br>
3.Name填写netease_username，Value填写 登录手机号<br>
4.再New secrets一个，Name填写netease_password，Value填写 登录密码<br>
5.再New secrets一个，Name填写SCKEY，Value填写Server酱推送SCKEY(可选，填过就不管)<br>
6.在"Actions"中的"run"下点击"Run workflow"即可手动执行签到，后续运行按照schedule，默认在每天凌晨0:30自动签到，可自行修改<br>
<br>
<br>
[腾讯云函数SCF](https://console.cloud.tencent.com/scf/index)的版本<br>
1.下载requirements.zip所需库，到[层](https://console.cloud.tencent.com/scf/layer)里面新建一个层<br>
2.到[函数服务](https://console.cloud.tencent.com/scf/list)里面新建一个函数，输入名字，运行环境选择python3.6，选择空白模板，下一步<br>
3.修改执行方法为index.main，修改index.py文件，把SCF版py文件内容覆盖掉里面的函数，删除config.json<br>
4.高级设置，添加多个环境变量key内输入：1.netease_username 2.netease_password 3.SCKEY(选填)<br>
value内输入：1.登录手机号 2.登录密码 3.Server酱推送SCKEY,报错提醒<br>
5.层配置，添加层，选择刚才新建的层。最后点完成<br>
6.进入函数→触发管理→新建触发器，按自己需求定时启动<br>
7.自己酌情修改函数的内存与执行超时时间以及其他参数<br>
