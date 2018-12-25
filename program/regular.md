- 字符串仅能是中文。
```
^[\\u4e00-\\u9fa5]{0,}$
```
- 密码的强度必须是包含大小写字母和数字的组合，不能使用特殊字符，长度在8-10之间。
```
^(?=.*\\d)(?=.*[a-z])(?=.*[A-Z]).{8,10}$
```
- 由数字、26个英文字母或下划线组成的字符串
```
^\\w+$
```
- 校验E-Mail 地址
```
[\\w!#$%&'*+/=?^_`{|}~-]+(?:\\.[\\w!#$%&'*+/=?^_`{|}~-]+)*@(?:[\\w](?:[\\w-]*[\\w])?\\.)+[\\w](?:[\\w-]*[\\w])?
```
- 下面是身份证号码的正则校验。15 或 18位。
```
// 15位
^[1-9]\\d{7}((0\\d)|(1[0-2]))(([0|1|2]\\d)|3[0-1])\\d{3}$
// 18位
^[1-9]\\d{5}[1-9]\\d{3}((0\\d)|(1[0-2]))(([0|1|2]\\d)|3[0-1])\\d{3}([0-9]|X)$
```
- “yyyy-mm-dd“ 格式的日期校验，已考虑平闰年
```
^(?:(?!0000)[0-9]{4}-(?:(?:0[1-9]|1[0-2])-(?:0[1-9]|1[0-9]|2[0-8])|(?:0[13-9]|1[0-2])-(?:29|30)|(?:0[13578]|1[02])-31)|(?:[0-9]{2}(?:0[48]|[2468][048]|[13579][26])|(?:0[48]|[2468][048]|[13579][26])00)-02-29)$
```
- 金额校验，精确到2位小数
```
^[0-9]+(.[0-9]{2})?$
```
- 下面是国内 13、15、18开头的手机号正则表达式。
```
^(13[0-9]|14[5|7]|15[0|1|2|3|5|6|7|8|9]|18[0|1|2|3|5|6|7|8|9])\\d{8}$
```
- IE目前还没被完全取代，很多页面还是需要做版本兼容，下面是IE版本检查的表达式
```
^.*MSIE [5-8](?:\\.[0-9]+)?(?!.*Trident\\/[5-9]\\.0).*$
```
- IP4 正则语句。
```
\\b(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\b
```

- IP6 正则语句。
```
(([0-9a-fA-F]{1,4}:){7,7}[0-9a-fA-F]{1,4}|([0-9a-fA-F]{1,4}:){1,7}:|([0-9a-fA-F]{1,4}:){1,6}:[0-9a-fA-F]{1,4}|([0-9a-fA-F]{1,4}:){1,5}(:[0-9a-fA-F]{1,4}){1,2}|([0-9a-fA-F]{1,4}:){1,4}(:[0-9a-fA-F]{1,4}){1,3}|([0-9a-fA-F]{1,4}:){1,3}(:[0-9a-fA-F]{1,4}){1,4}|([0-9a-fA-F]{1,4}:){1,2}(:[0-9a-fA-F]{1,4}){1,5}|[0-9a-fA-F]{1,4}:((:[0-9a-fA-F]{1,4}){1,6})|:((:[0-9a-fA-F]{1,4}){1,7}|:)|fe80:(:[0-9a-fA-F]{0,4}){0,4}%[0-9a-zA-Z]{1,}|::(ffff(:0{1,4}){0,1}:){0,1}((25[0-5]|(2[0-4]|1{0,1}[0-9]){0,1}[0-9])\\.){3,3}(25[0-5]|(2[0-4]|1{0,1}[0-9]){0,1}[0-9])|([0-9a-fA-F]{1,4}:){1,4}:((25[0-5]|(2[0-4]|1{0,1}[0-9]){0,1}[0-9])\\.){3,3}(25[0-5]|(2[0-4]|1{0,1}[0-9]){0,1}[0-9]))
```

- 下面的这个表达式可以筛选出一段文本中的URL。
```
^(f|ht){1}(tp|tps):\\/\\/([\\w-]+\\.)+[\\w-]+(\\/[\\w- ./?%&=]*)?
```

- 验证文件路径和扩展名
```
^([a-zA-Z]\\:|\\\\)\\\\([^\\\\]+\\\\)*[^\\/:*?"<>|]+\\.txt(l)?$
```

- 有时需要抽取网页中的颜色代码，可以使用下面的表达式。
```
\\#([a-fA-F]|[0-9]){3,6}
```

- 提取网页图片
```
\\< *[img][^\\>]*[src] *= *[\\"\\']{0,1}([^\\"\\'\\ >]*)
```

- 提取html中的超链接。
```
(]*)(href="https?://)((?!(?:(?:www\\.)?'.implode('|(?:www\\.)?', $follow_list).'))[^"]+)"((?!.*\\brel=)[^>]*)(?:[^>]*)>
```

- 匹配中文字符的正则表达式：
```
[\u4e00-\u9fa5]
```

- 匹配双字节字符(包括汉字在内)：
```
[^\x00-\xff]
```

- 匹配空行的正则表达式：
```
\n[\s| ]*\r
```

- 匹配HTML标记的正则表达式
```
/<(.*)>.*<\/\1>|<(.*) \/>/
```

- 匹配首尾空格的正则表达式：
```
(^\s*)|(\s*$)
```

- 匹配Email地址的正则表达式：
```
\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*
```

- 匹配网址URL的正则表达式：
```
^[a-zA-z]+://(\\w+(-\\w+)*)(\\.(\\w+(-\\w+)*))*(\\?\\S*)?$
```

- 匹配帐号是否合法(字母开头，允许5-16字节，允许字母数字下划线)：
```
^[a-zA-Z][a-zA-Z0-9_]{4,15}$
```

- 匹配国内电话号码：
```
(\d{3}-|\d{4}-)?(\d{8}|\d{7})?
```

- 匹配腾讯QQ号：
```
^[1-9]*[1-9][0-9]*$
```