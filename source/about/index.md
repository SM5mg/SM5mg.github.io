---
seo_title: 关于我
menu_id: more
h1: ''
breadcrumb: false # 隐藏
title: 关于我
leftbar: [linklist, memos-du] # linklist,ghuser,引入github 名片
rightbar: [new_comment]
---
{% banner 耶 bg:/assets/images/friends.webp %}
{% endbanner %}

<h4 style="font-family: 'Gloria Hallelujah';text-align: center;display: block; color:#7979ec ">{% emoji height:1.5em blobcat ablobcatwave %} Hi ~ It's a pleasure to meet you ! </h4>

<center>
{% box ✨人海茫茫，恭喜你发现我了。 color:blue child:codeblock/tabs %}
{% swiper effect:coverflow width:min %}
{% image https://s2.loli.net/2024/12/04/AbIEYeVtgyWKDFP.jpg %}
{% image https://s2.loli.net/2024/12/04/54zprN826DQCdfO.jpg %}
{% image https://s2.loli.net/2024/12/04/uftkFqWVJYaDijd.jpg %}
{% image https://s2.loli.net/2024/12/04/HyLeXOUNB2vSc6P.jpg %}
{% image https://s2.loli.net/2024/12/04/7uAKjvyozb1lZnI.jpg %}
{% endswiper %}
<p style="text-align:center;font-weight: bold;"><span style="font-size:1.2em;">MBTI:</span><span  style="font-size:1.2em; color: #ec4a13;"> <a href="https://www.16personalities.com/ch/enfp-%E4%BA%BA%E6%A0%BC" target="_blank">ENFP</a></span></p>
{% hashtag 快乐小狗  color:purple %}
{% hashtag 反内耗 color:orange  %}
{% hashtag 真诚热情  color:yellow %}
{% hashtag 三分钟热度  color:green %}
{% hashtag 直球选手 %}
<p class="p-center">
一个<emp>热衷于瞎折腾</emp>的庸人。
<br>
<br>人来疯，间歇性emo ;
<br>喜欢喧嚣，同样爱着寂静自然，经常爬山，徒步，骑车…
<br>生性乐观，神经大条却又极度敏感，听悲伤的歌，看悲情的剧；
<br>容易躁动，听最摇滚的歌，看最恐怖的电影；
<br>享受独处的时光，热爱一群人的狂欢。
<br>
<br>" <u><strong>永远年轻，永远好奇</strong></u> ！"
</p>
{% endbox %}</center>

#### 伙伴集结
---
{% friends api:https://api.vlts.cc/output_data/v2/sumorio/friends %}
---
#### **Ta们的文章更新啦**

{% box child:tabs %}
{% tabs %}
<!-- tab  友之文 -->
{% timeline type:fcircle limit:8 api:https://raw.githubusercontent.com/Sumorio/hexo-circle-of-friends/refs/heads/output/data.json  %}
{% endtimeline %}
<!-- tab 探索号 -->
{% timeline hide:title,footer api:https://api.github.com/repos/xaoxuu/hexo-theme-stellar/issues?state=all&labels=分享&per_page=5 %}
{% endtimeline %}
{% endtabs %}
{% endbox %}


{% quot 想成为我的小伙伴？  %}

{% tabs active:1 align:center %}

<!-- tab 小小请求 -->
<br>
{% checkbox checked:true  先友后链：有效互动大于1次，issue或者留言。 %}
{% checkbox checked:true  安全合规：合法网站，非纯搬运，非盈利，无木马植入的站点。%}
{% checkbox checked:true  有效网站：至少2篇原创文章；能正常访问。%}
{% checkbox symbol:times color:red checked:true  其他原则：若您的网站长期不更新、存在广告等情况，可能会暂时下架。%}
<br>
<!-- tab 申请步骤 -->
{% timeline %}
<!-- node 1.  新建 Issue.  -->
点击{% button Issues  https://github.com/Sumorio/friends/issues/  size:xs %}→`New Issues`→`Get Started`→填写您的站点信息→提交。

<!-- node 2. 将本站点添加至您的友链仓库中。 -->
```
{
    "title": "薩魔5mg",
    "url": "https://5mg.fun/",
    "avatar": "https://s2.loli.net/2024/11/29/RKTqupPVzO17elL.png"
}
```
<!-- node 3. 等待站长审核通过，刷新该网页即可呈现您的友链。 -->

{% emoji height:1.5em blobcat ablobcatattentionreverse %} 如需更新友链，前往{% button Issues  https://github.com/Sumorio/friends/issues/  size:xs %}提交处，留言告知。

{% endtimeline %}
{% endtabs %}

{% quot 留言区 icon:hashtag %}