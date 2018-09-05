# 🎮 中文 DOS 游戏

浏览器游玩中文 DOS 游戏

## 运行
python3执行
```
# encoding=utf8
import urllib.request, os

from urllib.parse   import quote
from urllib.request import urlopen

from game_infos import game_infos

PREFIX = "https://dos.zczc.cz/static/gamedata/"
DESTINATION = os.path.normcase('static/gamedata/')

for identifier in game_infos['games'].keys():
    #urllib.request.urlretrieve(PREFIX + identifier + '.zip', os.path.join(DESTINATION, identifier + '.zip'))
    url = PREFIX + quote(identifier) + '.zip'
    path = os.path.join(DESTINATION, identifier + '.zip').encode('utf-8')
    urllib.request.urlretrieve(url,path)
```


首先编译 `em-dosbox`，编译方法参见 [dreamlayers/em-dosbox: An Emscripten port of DOSBox](https://github.com/dreamlayers/em-dosbox)。将编译出的 `em-dosbox/src/dosbox.js` 和 `em-dosbox/src/dosbox.html.mem` 移动至 `static/dosbox` 文件夹下。然后运行 `generate.py` 生成 `game.data` 文件。最后运行 `app.py`

## 游戏列表

* 仙剑奇侠传
* 模拟城市 2000
* 美少女梦工厂
* 同级生 2
* 大富翁3
* 明星志愿1
* 三国志IV
* 金庸群侠传
* 轩辕剑1
* 轩辕剑2
* 皇帝
* 轩辕剑外传：枫之舞
* 疯狂医院
* 大航海时代
* 大航海时代2
* 银河英雄传说III SP
* 三国志II
* 三国志III
* 三国志V
* 三国志V 威力加强版
* 三国志英杰传
* 主题医院
* 三国演义
* 三界谕：邦沛之迷
* 殖民计划
* 炎龙骑士团II‧黄金城之谜
* 倚天屠龙记
* 信长之野望·天翔记
* 信长之野望·霸王传
* 金瓶梅之偷情宝鉴


## Known issues

* 游戏界面在游戏运行时会改变 `<title>`
* `packager.py` 产生的 Javascript 脚本包含主机的路径信息，需要去除。

## Contributing

欢迎提 Issue 和 Pull request 来增加新的游戏!

## Credits
[dreamlayers/em-dosbox: An Emscripten port of DOSBox](https://github.com/dreamlayers/em-dosbox)
