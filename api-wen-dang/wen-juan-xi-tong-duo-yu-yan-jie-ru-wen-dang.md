# 问卷系统多语言接入文档

##

### 1.接口说明

游戏客户端自行接入多语言传参，投放多语言问卷时，动态拼接language参数到投放链接，实现根据传参语言自动显示对应语言问卷。

### 2. 功能说明

问卷系统支持游戏侧传递语言参数给问卷侧，打开问卷时自动显示对应语言问卷，需要游戏客户端在打开问卷时传递当前语言参数(`language`)。如果未传递此参数，问卷将显示预设的默认语言。

### 3. 链接示意

&#x20;基础问卷链接

<pre><code><strong>国内：https://in.weisurvey.com/v2/?sid=686f8b311a3a28274eee3db6
</strong><strong>海外：https://user.outweisurvey.com/v2/?sid=685bc4b94e2cdb66de0fc6ae
</strong></code></pre>

要实现多语言显示，需要在基础链接后追加`language`参数，格式如下：

<pre><code>国内：https://in.weisurvey.com/v2/?sid=686f8b311a3a28274eee3db6&#x26;language=en
<strong>海外：https://user.outweisurvey.com/v2/?sid=685bc4b94e2cdb66de0fc6ae&#x26;language=en
</strong></code></pre>

### 4.语言代码示例 &#x20;

<table><thead><tr><th width="128.99993896484375">序号</th><th>语言代码</th><th>语言</th></tr></thead><tbody><tr><td>1</td><td>en</td><td>英语</td></tr><tr><td>2</td><td>zh-CHS</td><td>中文简体</td></tr><tr><td>3</td><td>zh-CHT</td><td>中文繁体</td></tr><tr><td>4</td><td>zh-HK</td><td>中文繁体（中国香港）</td></tr><tr><td>5</td><td>zh-TW</td><td>中文繁体（中国台湾）</td></tr><tr><td>6</td><td>ar</td><td>阿拉伯语</td></tr><tr><td>7</td><td>de</td><td>德语</td></tr><tr><td>8</td><td>ru</td><td>俄语</td></tr><tr><td>9</td><td>fr</td><td>法语</td></tr><tr><td>10</td><td>phi</td><td>菲律宾语</td></tr><tr><td>11</td><td>ko</td><td>韩语</td></tr><tr><td>12</td><td>km</td><td>高棉语</td></tr><tr><td>13</td><td>ms</td><td>马来语</td></tr><tr><td>14</td><td>bn</td><td>孟加拉语</td></tr><tr><td>15</td><td>pt</td><td>葡萄牙语</td></tr><tr><td>16</td><td>ja</td><td>日语</td></tr><tr><td>17</td><td>th</td><td>泰语</td></tr><tr><td>18</td><td>tr</td><td>土耳其语</td></tr><tr><td>19</td><td>ur</td><td>乌尔都语</td></tr><tr><td>20</td><td>es</td><td>西班牙语</td></tr><tr><td>21</td><td>it</td><td>意大利语</td></tr><tr><td>22</td><td>hi</td><td>印地语</td></tr><tr><td>23</td><td>id</td><td>印尼语</td></tr><tr><td>24</td><td>vi</td><td>越南语</td></tr><tr><td>25</td><td>uz</td><td>乌兹别克语</td></tr></tbody></table>

### 5. 实现步骤

1. 获取游戏当前语言设置
2. 将当前语言转换为问卷系统支持的语言代码
3. 将语言代码拼接到问卷链接中
4. 在游戏内打开拼接后的完整链接



### 6. 注意事项

1. 请确保传递的语言代码是问卷系统支持的语言之一
2. 如果传递的语言代码问卷系统不支持，将显示默认语言
3. 语言代码区分大小写，请使用正确的大小写格式
4. 参数必须使用`&language=`格式拼接在URL后

