# 登录态回调接口(IDIP)

## 1. 接口说明

### 1.1 接口定义

用户提交问卷后，问卷系统将登录态等参数回调给开发者，适用于奖励发放、业务状态修改等场景。

### 1.2 使用场景

适用于开发者接入问卷系统后，无法接入 [登录态回调接口(HTTP)](deng-lu-tai-hui-tiao-jie-kou.md)， 但是又需要用户在答题之后将用户等相关信息**回传给开发者服务端**的情况。

请注意，如果配置了 IDIP回调，HTTP 回调的配置会默认失效，问卷服务优先处理 IDIP。

## 2. 回调说明

### 2.1 接口自定义参数配置

#### 2.1.1 基础配置

#### 2.1.2 参数配置

在 `接口自定义参数` 中支持两种参数占位符：

1.  前端参数占位符(打开问卷链接时注入)：`{key}`

    * 格式：`{参数名}`&#x20;
    * 说明：从问卷前端传入的 query 参数中获取值
    * 示例：`a=1&b={b}&c=3`


2. 答题信息占位符(问卷系统内置字段)：`[key]`
   * 格式：`[参数名]`&#x20;
   * 说明：从问卷系统内部获取，是固定值
   * 支持的参数：
     * `[effective]`: 问卷有效性（0: 有效，非0: 无效）
     * `[answer_consumed]`: 答题耗时（秒）
     * `[uid_info]`: 用户信息
   * 示例：`a=1&effective=[effective]&uid_info=[uid_info]`

#### 2.1.3 完整参数配置示例

```
type=1&userSource={userSource}&effective=[effective]&uid_info=[uid_info]
```

配置说明：

1. _`type=1`: 固定值，用于标识请求类型_
2. _`userSource={userSource}`: 从问卷前端传入的参数，问卷打开的时候客户端注入，例如：`userSource=test_value`_
3. _`effective=[effective]`: 问卷有效性标记 ，来源于问卷系统的字段定义_
   * _0: 有效问卷_
   * _非0: 无效问卷_
4. _`uid_info=[uid_info]`: 用户信息，来源于问卷系统的字段定义_
5. _`answer_consumed=[answer_consumed]`: 答题耗时（秒），来源于问卷系统的字段定义_

### 2.2 回调成功约定返回格式

#### 2.2.1 响应格式

```
result=0&error_info=success
```

#### 2.2.2 响应参数说明

* `result`: 回调结果
  * `0`: 回调成功
  * 其他值: 回调失败
* `error_info`: 错误信息
  * 成功时返回 "success"
  * 失败时返回具体错误信息

#### 2.2.3 示例

```
# 成功响应
result=0&error_info=success

# 失败响应
result=1&error_info=invalid_parameter
```

## 3. 回调接口调试工具

可使用回调接口调试工具（建议使用chrome打开）确认调通回调与签名验证。

【国内】[https://test.a.imur.tencent.com/static/tools/index.html#/callback](https://test.a.imur.tencent.com/static/tools/index.html#/callback/log)

【海外】[https://test.a.imur.tencent.com/static/tools-out/#/callback](https://test.a.imur.tencent.com/static/tools-out/#/callback/log)

## 4. 回调记录查询

系统提供工具用于查询问卷服务端发起回调的记录和回调参数，请根据所属环境使用

【国内】[https://test.a.imur.tencent.com/static/tools/index.html#/callback/log](https://test.a.imur.tencent.com/static/tools/index.html#/callback/log)

【海外】[https://test.a.imur.tencent.com/static/tools-out/#/callback/log](https://test.a.imur.tencent.com/static/tools-out/#/callback/log)
