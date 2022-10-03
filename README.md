# API Reference
> 这里是d0j1a_1701的API文档
> 
> 如果你不知道d0j1a_1701是什么 请跳进这个传送门:
> 
> [d0j1a_1701的主页](https://d0j1a1701.cc)

## Key-Value 存储器

可在短时间存储一个键值对，类似于C++的`std::map<string,string>`。

存储有效期为1小时。

### 读取

> URL: `api.d0j1a1701.cc/kv/{key}`
> 
> method: `GET`

- 若成功，返回200，并返回键值对的值。
- 若失败，返回404，并返回错误信息`Value not found`。

```javascript
fetch(`https://api.d0j1a1701.cc/kv/${key}`)
	.then(resp => resp.text())
	.then(res => console.log(res))
	.catch(err => console.error(err));
```

### 写入

> URL: `api.d0j1a1701.cc/kv/{key}`
>
> method: `POST`

- 若成功，返回200，并返回新插入键值对的值。
- 如果这个`key`已被使用，则覆盖原值。

```javascript
fetch(`https://api.d0j1a1701.cc/kv/${key}`, {
	method: "POST",
	body: value
})  .then(resp => resp.text())
    .then(res => console.log(res))
    .catch(error => {console.error(error)});
```

## 随机图片

> Base-URL: https://api.d0j1a1701.cc/random/

返回[d0j1a1701/randpic-imghost](https://github.com/d0j1a1701/randpic-imghost)中随机的一张图片。

- 禁用缓存(`Cache-Control: no-store`)
- 图片格式为webp(`Content-type: image/webp`)
- 加入`?cover=true`参数可限制图片宽度为720px，可作为博客封面

效果如下:

![](https://api.d0j1a1701.cc/random/)

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
