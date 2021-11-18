# balloon
B站直播弹幕命令行版

**目前提供release，整理后开源。**

## 使用

```bash
./balloon 510
```

效果:

![效果图](images/1.gif)

## 发送弹幕功能

当前目录下存在`credential.json`时，会试图读取，成功后拥有发送弹幕功能。

`credential.json`格式:

```json
{
  "SESSDATA": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "buvid3": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXXXXXXXXinfoc",
  "bili_jct": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

可以使用如下JS代码，在[B站](https://www.bilibili.com)打开F12获取，其中`SESSDATA`无法通过JS获取,需要在F12-Application-Storage-Cookies中搜索`SESSDATA`,并将对应的Value值手动复制到json文件中.

```javascript
console.log(JSON.stringify(document.cookie.split(';').reduce((prev, current) => {
    const [k, v] = current.split('=').map(v => v.trim());
    return (k === 'bili_jct' || k === 'buvid3') ? {...prev, [k]: v}: prev ;
}, {"SESSDATA":""}), null, 2))

```

保存为`credential.json`后放到同级目录下即可.

