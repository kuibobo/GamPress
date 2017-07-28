# GamPress
一个WordPress插件

集成SNS登录组件(微信,微薄,QQ,短信), 

Pay组件(支付宝,微信支付), 

Activity留言模块, 

Notification通知模块, 

Votes投票模块

Members模块
=========================
## 安装并激活.
1)将GamPress目录放置到WordPress的Plugins目录
2)在WordPress后台激活
3)在GamPress设置里里面填入社交模块的appId和secret.

##在您的模板中使用
1)SNS登录
``` HTML
<a href="/sns/oauth/qq?callback=<?php echo $redirect;?>" class="qq">QQ</a>
<a href="/sns/oauth/wechat?callback=<?php echo $redirect;?>" class="wx">微信</a>
<a href="/sns/oauth/weibo?callback=<?php echo $redirect;?>" class="wb">微博</a>
``` 
2)支付
``` HTML
<form method="post" action="/orders/create?redirect=<?php echo $redirect;?>" class="form-box">
    <input type="hidden" name="product_id" id="product_id" value="0" />
    <input type="hidden" name="item_id" id="item_id" value="0" />
    <input type="hidden" name="price" id="price" value="0.01" />
    <input type="hidden" name="quantity" id="quantity" value="1" />
    <input type="hidden" name="total_fee" id="total_fee" value="0.01" />
    <input type="hidden" name="pay_module" id="pay_module" value="wechat" />
    <input type="hidden" name="product_name" id="product_name" value="订单名称" />
    <input type="hidden" name="product_description" id="product_description" value="订单描述" />
</form>
``` 
3) 微信分享代码
```PHP
<?php
$protocol = (!empty($_SERVER['HTTPS']) && $_SERVER['HTTPS'] !== 'off' || $_SERVER['SERVER_PORT'] == 443) ? "https://" : "http://";
$link = "$protocol$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]";
$title = wp_title( '&lsaquo;', false, 'right' );
$desc = gp_get_description();
$icon = '';
gp_wechat_share( $link, $title, $desc, $icon );
?>

```

## 感谢
感谢BuddyPress. 插件的实现机制跟BuddyPress一样,并且部分代码来至BuddyPress


