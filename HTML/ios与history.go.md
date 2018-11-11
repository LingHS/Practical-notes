# ios不支持window.history.go方法
  
> 在vue项目中使用this.$router.go(-1) 不生效

上网搜索后发现
加上return false;   

`<a href="#" class="back" onclick="javascript: window.history.go(-1);return false;"></a>`  

可解决问题

至于vue的项目中,则换用back()