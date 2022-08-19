# API Reference
> 这里是d0j1a_1701的API文档
> 
> 如果你不知道d0j1a_1701是什么 请跳进这个传送门:
> 
> [d0j1a_1701的主页](https://d0j1a1701.cc)

## Key-Value 存储器
> Base-URL: https://kv.d0j1a1701.cc

可在短时间存储一个键值对，类似于C++的`std::map<string,string>`。

存储有效期为1小时。

### 读取

> URL: `/{key}`
> 
> method: `GET`

- 若成功，返回200，并返回键值对的值。
- 若失败，返回404，并返回错误信息`Value not found`。

```javascript
fetch(`https://kv.d0j1a1701.cc/${key}`)
	.then(resp => resp.text())
	.then(res => console.log(res))
	.catch(err => console.error(err));
```

### 写入

> URL: `/{key}`
>
> method: `POST`

- 若成功，返回200，并返回新插入键值对的值。
- 如果这个`key`已被使用，则覆盖原值。

```javascript
fetch(`https://kv.d0j1a1701.cc/${key}`, {
	method: "POST",
	body: value
})  .then(resp => resp.text())
    .then(res => console.log(res))
    .catch(error => {console.error(error)});
```

## 随机图片

### 普通

> Base-URL: https://random.d0j1a1701.cc

返回[dajia-1701/randpic-imghost](https://github.com/dajia-1701/randpic-imghost)中随机的一张图片。

- 禁用缓存(`Cache-Control: no-store`)`
- 图片格式为webp(`Content-type: image/webp`),

> 虽然`Headers`里禁用缓存，但同一页面下放入多个随机图仍然可能会被缓存（全部图片都是一样的），因此建议使用JS在每张图片地址后加入随机数做参数强制取消缓存。

效果如下:

![](https://random.d0j1a1701.cc)

### 封面

> Base-URL: https://bg.d0j1a1701.cc

同 https://random.d0j1a1701.cc 但图片经过剪切可作为[博客](https://www.d0j1a1701.cc)封面。

![](https://bg.d0j1a1701.cc)

## Luogu 个人资料卡

> Base-URL: https://luogu-card.d0j1a1701.cc

### 基本信息

```markdown
![你的基本信息](https://luogu-card.d0j1a1701.cc/about?id=你的用户编号)
```

效果

![d0j1a_1701的基本信息](https://luogu-card.d0j1a1701.cc/about?id=248302)

### 练习情况

```markdown
![你的练习情况](https://luogu-card.d0j1a1701.cc/practice?id=你的用户编号)
```

效果

![d0j1a_1701的练习情况](https://luogu-card.d0j1a1701.cc/practice?id=248302)

### 咕值信息

手动填入，复制代码的时候记着改`URL`

```markdown
![你的咕值信息](https://luogu-card.d0j1a1701.cc/guzhi?id=你的用户编号&scores=基础信用,练习情况,社区贡献,比赛情况,获得成就)
```

效果

![d0j1a_1701的咕值信息](https://luogu-card.d0j1a1701.cc/guzhi?id=248302&scores=100,40,2,2,30)

### 自定义选项

#### 隐藏标题

`URL`末尾加上`&hide_title=true`

```markdown
![你的基本信息](https://luogu-card.d0j1a1701.cc/about?id=你的用户编号&hide_title=true)
```

效果

![d0j1a_1701的基本信息](https://luogu-card.d0j1a1701.cc/about?id=248302&hide_title=true)

#### 暗黑模式

`URL`末尾加上`&dark_mode=true`

```markdown
![你的基本信息](https://luogu-card.d0j1a1701.cc/about?id=你的用户编号&dark_mode=true)
```

效果

![d0j1a_1701的基本信息](https://luogu-card.d0j1a1701.cc/about?id=248302&dark_mode=true)

#### 自定义宽度

`URL`末尾加上`&card_width=需要的宽度`

```markdown
![你的基本信息](https://luogu-card.d0j1a1701.cc/about?id=你的用户编号&card_width=需要的宽度)
```

效果

![d0j1a_1701的基本信息](https://luogu-card.d0j1a1701.cc/about?id=248302&card_width=750)

#### 禁用缓存

`URL`末尾加上`&disable_cache=true`

为了防止滥用`luogu`流量~~导致kkk扬了你IP~~本工具默认有`12h`的缓存(白话文:每12小时更新一次数据)。

#### 叠加使用

全部的自定义选项均可叠加：

```markdown
![d0j1a_1701的基本信息](https://luogu-card.d0j1a1701.cc/about?id=248302&hide_title=true&dark_mode=true&card_width=750)
```

效果

![d0j1a_1701的基本信息](https://luogu-card.d0j1a1701.cc/about?id=248302&hide_title=true&dark_mode=true&card_width=750)

## Visual Judge 镜像

https://vjudge.d0j1a1701.cc

通过[Vercel](https://vercel.com)反向代理`Visual Judge`提升中国大陆用户的访问速度。

## 在线 IDE

https://ide.d0j1a1701.cc

在线编译运行C++代码。

- 编译参数: `-std=c++20 -O2`
- 使用了[Coliru](https://coliru.stacked-crooked.com/)的在线编译运行API
- 可生成临时链接分享代码(使用`Key-Value存储器`API)

## Github 下载加速

https://gh.d0j1a1701.cc

`Cloudflare Worker`反向代理`Github`，加速下载。
