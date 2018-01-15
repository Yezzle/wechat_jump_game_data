# wechat_jump_game_data

微信跳一跳自动生成游戏数据，并发送请求。目前使用[样本数据](./data/game_data.js)构造 
game_data 数据，按后台加密规则加密后发送请求。
由于 **game_data 的后台验证机制暂不明朗**，存在请求提交正常但成绩未录入的情况(很无奈)。

> `dev` 分支 `game_data` 构造方法调整，若在 `./data/raw` 中存在已有真实数据，则不构造数据，直接使用
之前的 `game_data` 加密后发送至服务器端(通过验证几率较高)。

## 使用方法

1. 安装 [node](https://github.com/nodejs/node) (建议安装 8.0 及以上版本)
2. 使用 [whistle](https://github.com/avwo/whistle) 或抓包工具抓取 `session_id`  
   1. 安装后在命令行使用 `w2 start` 启动 `whistle`
   2. 手机设置 http 代理为上一步弹出的 IP 地址
   3. 在管理页面，点击 `Https` 手机扫描二维码或使用浏览器输入对应地址，下载根证书
   4. 信任根证书后，勾选 `Intercept HTTPS CONNECTs`
   5. 进去游戏，任意 `/wxagame` 开头的请求在 `Request` 内即可看到 `session_id`
3. 在 `config.js` 内填入 `session_id` 和想提交的分数 `score` (目前经验值是 10 - 999 为安全数据)

4. 安装依赖：

```bash
$ npm install
```

5. 生成数据并提交微信后台：

```bash
$ npm start
```

## TODO

- [x] 补充注释及简单说明
- [x] 补充 session_id 抓取方法
- [ ] Web 管理页面
- [ ] 简单范围校验判断

## 实验结果

```bash
# 更新时间 2018年01月15日13点20分
# 目前样本数据包含 696 | 762 | 945 | 995 | 1201 分的历史数据
# 696 | 697 | 698 | 762 | 945 | 995 均被服务器接受
# 699 | 761 | 763 | 944 | 946 | 994 | 996 | 1201 未被服务器接受
Ver***:wechat_jump_game_data Rai***$ node index.js 696
当前周最高分: 81
当前游戏次数: 66
准备构造第 67 次游戏 696 分的请求数据
成绩已成功提交至服务器
当前周最高分: 696
当前游戏次数: 67
Ver***:wechat_jump_game_data Rai***$ node index.js 697
当前周最高分: 696
当前游戏次数: 67
准备构造第 68 次游戏 697 分的请求数据
成绩已成功提交至服务器
当前周最高分: 697
当前游戏次数: 68
Ver***:wechat_jump_game_data Rai***$ node index.js 698
当前周最高分: 697
当前游戏次数: 68
准备构造第 69 次游戏 698 分的请求数据
成绩已成功提交至服务器
当前周最高分: 698
当前游戏次数: 69
Ver***:wechat_jump_game_data Rai***$ node index.js 699
当前周最高分: 698
当前游戏次数: 69
准备构造第 70 次游戏 699 分的请求数据
成绩已成功提交至服务器
当前周最高分: 698
当前游戏次数: 69
Ver***:wechat_jump_game_data Rai***$ node index.js 760
当前周最高分: 698
当前游戏次数: 69
准备构造第 70 次游戏 760 分的请求数据
成绩已成功提交至服务器
当前周最高分: 698
当前游戏次数: 69
Ver***:wechat_jump_game_data Rai***$ node index.js 761
当前周最高分: 698
当前游戏次数: 69
准备构造第 70 次游戏 761 分的请求数据
成绩已成功提交至服务器
当前周最高分: 698
当前游戏次数: 69
Ver***:wechat_jump_game_data Rai***$ node index.js 762
当前周最高分: 698
当前游戏次数: 69
准备构造第 70 次游戏 762 分的请求数据
成绩已成功提交至服务器
当前周最高分: 762
当前游戏次数: 70
Ver***:wechat_jump_game_data Rai***$ node index.js 763
当前周最高分: 762
当前游戏次数: 70
准备构造第 71 次游戏 763 分的请求数据
成绩已成功提交至服务器
当前周最高分: 762
当前游戏次数: 70
Ver***:wechat_jump_game_data Rai***$ node index.js 764
当前周最高分: 762
当前游戏次数: 70
准备构造第 71 次游戏 764 分的请求数据
成绩已成功提交至服务器
当前周最高分: 762
当前游戏次数: 70
Ver***:wechat_jump_game_data Rai***$ node index.js 944
当前周最高分: 762
当前游戏次数: 75
准备构造第 76 次游戏 944 分的请求数据
成绩已成功提交至服务器
当前周最高分: 762
当前游戏次数: 75
Ver***:wechat_jump_game_data Rai***$ node index.js 945
当前周最高分: 762
当前游戏次数: 75
准备构造第 76 次游戏 945 分的请求数据
成绩已成功提交至服务器
当前周最高分: 945
当前游戏次数: 76
Ver***:wechat_jump_game_data Rai***$ node index.js 946
当前周最高分: 945
当前游戏次数: 76
准备构造第 77 次游戏 946 分的请求数据
成绩已成功提交至服务器
当前周最高分: 945
当前游戏次数: 76
Ver***:wechat_jump_game_data Rai***$ node index.js 994
当前周最高分: 945
当前游戏次数: 76
准备构造第 77 次游戏 994 分的请求数据
成绩已成功提交至服务器
当前周最高分: 945
当前游戏次数: 76
Ver***:wechat_jump_game_data Rai***$ node index.js 995
当前周最高分: 945
当前游戏次数: 76
准备构造第 77 次游戏 995 分的请求数据
成绩已成功提交至服务器
当前周最高分: 995
当前游戏次数: 77
Ver***:wechat_jump_game_data Rai***$ node index.js 996
当前周最高分: 995
当前游戏次数: 77
准备构造第 78 次游戏 996 分的请求数据
成绩已成功提交至服务器
当前周最高分: 995
当前游戏次数: 77
Ver***:wechat_jump_game_data Rai***$ node index.js 1201
当前周最高分: 995
当前游戏次数: 77
准备构造第 78 次游戏 1201 分的请求数据
成绩已成功提交至服务器
当前周最高分: 995
当前游戏次数: 77
```
