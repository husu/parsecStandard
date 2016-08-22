# 秒差距接口规范
###文档目的

* 建立公司后端接口编写规范，降低前后端不必要的沟通成本。
* 通过接口的一致性，确保代码复用。
* 规范输入和输出

### 修改记录

<table>
<tr>
	<td>版本</td>
	<td>日期</td>
	<td>内容</td>
</tr>
<tr>
	<td>0.1</td>
	<td>2016年8月22日</td>
	<td>创建接口文档</td>
</tr>
</table>

### 输入规范

输入参数接受如下数据类型

- 数字
- 字符
- 数组
- 日期：以长整形传输
- 布尔

例如：
> {
	createdAt:1461943200000,
	goods:[{name:'商品1',price:13.45},{name:'商品2',price:13.45}]
	}

注：
- 输入应尽量减少参数为对象的情况，例如
>{user:{name:'zhangsan',age:17,gender:'男'}

### 输出规范
- 输出数据格式一定为JSON
- 输出数据格式包括以下字段

<table>
<tr>
	<td>参数</td>
	<td>说明</td>
		<td>类型</td>
</tr>
<tr>
	<td>code</td>
	<td>状态编码</td>
	<td>类型</td>
</tr>
<tr>
	<td>message</td>
	<td>消息</td>
	<td>需要在前端显示的消息，此消息应相对友好</td>
</tr>
<tr>
	<td>result</td>
	<td>结果数据</td>
	<td>类型接受：日期（长整形）、数字、字符、数组、对象</td>
</tr>
<tr>
	<td>errors</td>
	<td>错误的详细信息(可选)</td>
	<td>类型接受：字符串</td>
</tr>
</table>

注：
* 如果返回值中存在百分数，统一采用小数形式返回
* errors不是必须的，主要在开发阶段为debug提供信息，在上线后尽量消除
* result里的对象属性若只有一个，建议直接放置属性值


例如
不推荐：
    `{code：0,message:'保存成功',result:{id:233121212}}`
推荐
    `{code：0,message:'保存成功',result:233121212}`



#### 关于code的规范

code属性为状态码，定义 0 为正确，正数为公有错误码，负数为私有错误码。


<table>
<tr>
	<td>编码</td>
	<td>说明</td>
</tr>
<tr>
	<td>0</td>
	<td>处理成功</td>
</tr>
<tr>
	<td>1</td>
	<td>错误信息。。</td>
</tr>
</table>

