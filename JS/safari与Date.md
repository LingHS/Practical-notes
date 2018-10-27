# safari下的Date

>踩到了safari浏览器的一个坑,不支持横杠

`new Date('2018-10-27 17:47:04')     // Invalid Date  `

解决方法：正则替换
将`-`变成`/`  
`new Date('2018-10-27 17:47:04').replace(/-/g,'/') `