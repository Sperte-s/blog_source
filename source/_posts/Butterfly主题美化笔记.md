---
title: Butterfly主题美化笔记
abbrlink: 40304
date: 2022-05-11 08:35:13
tags: 
- 笔记
- 教程
categories: 经验
description: '记录主题的魔改历程'
swiper_index: 4
cover: https://cdn.jsdelivr.net/gh/Sperte-s/img/建站历程.webp
---
## 前言

记录一下我的主题魔改历程，便于以后修改。
美化不涉及主题源码，只涉及插件和css挂载。

`_config.yml`路径为`[博客根目录]/`
`_config.butterfly.yml`路径为`[博客根目录]/`

------------------

## Ⅰ.自定义CSS

在`[博客根目录]/themes/butterfly/source/css/`处新建`custom.css`文件

### 背景图渐变效果

在`custom.css`中添加

```css
/*！背景图渐变效果*/
#body-wrap {
  background: -webkit-linear-gradient(
    0deg,
    rgba(247, 149, 51, 0.1) 0,
    rgba(243, 112, 85, 0.1) 15%,
    rgba(239, 78, 123, 0.1) 30%,
    rgba(161, 102, 171, 0.1) 44%,
    rgba(80, 115, 184, 0.1) 58%,
    rgba(16, 152, 173, 0.1) 72%,
    rgba(7, 179, 155, 0.1) 86%,
    rgba(109, 186, 130, 0.1) 100%
  );
  background: -moz-linear-gradient(
    0deg,
    rgba(247, 149, 51, 0.1) 0,
    rgba(243, 112, 85, 0.1) 15%,
    rgba(239, 78, 123, 0.1) 30%,
    rgba(161, 102, 171, 0.1) 44%,
    rgba(80, 115, 184, 0.1) 58%,
    rgba(16, 152, 173, 0.1) 72%,
    rgba(7, 179, 155, 0.1) 86%,
    rgba(109, 186, 130, 0.1) 100%
  );
  background: -o-linear-gradient(
    0deg,
    rgba(247, 149, 51, 0.1) 0,
    rgba(243, 112, 85, 0.1) 15%,
    rgba(239, 78, 123, 0.1) 30%,
    rgba(161, 102, 171, 0.1) 44%,
    rgba(80, 115, 184, 0.1) 58%,
    rgba(16, 152, 173, 0.1) 72%,
    rgba(7, 179, 155, 0.1) 86%,
    rgba(109, 186, 130, 0.1) 100%
  );
  background: -ms-linear-gradient(
    0deg,
    rgba(247, 149, 51, 0.1) 0,
    rgba(243, 112, 85, 0.1) 15%,
    rgba(239, 78, 123, 0.1) 30%,
    rgba(161, 102, 171, 0.1) 44%,
    rgba(80, 115, 184, 0.1) 58%,
    rgba(16, 152, 173, 0.1) 72%,
    rgba(7, 179, 155, 0.1) 86%,
    rgba(109, 186, 130, 0.1) 100%
  );
  background: linear-gradient(
    90deg,
    rgba(247, 149, 51, 0.1) 0,
    rgba(243, 112, 85, 0.1) 15%,
    rgba(239, 78, 123, 0.1) 30%,
    rgba(161, 102, 171, 0.1) 44%,
    rgba(80, 115, 184, 0.1) 58%,
    rgba(16, 152, 173, 0.1) 72%,
    rgba(7, 179, 155, 0.1) 86%,
    rgba(109, 186, 130, 0.1) 100%
  );
}
```

### 透明度调整

在`custom.css`中添加

```css
/*页脚透明度调整*/
#footer {
  opacity: 0.9;
}
/* 页脚透明 */
#footer {
  background: transparent !important;
}
/* 页脚黑色透明玻璃效果移除 */
#footer::before {
  background: transparent !important;
}
/* 头图透明 */
#page-header {
  background: transparent !important;
}
/* 头图遮罩层透明 */
#page-header::before {
  background: transparent !important;
}
/*top-img黑色透明玻璃效果 */
#page-header.post-bg:before {
  background-color: transparent !important;
}
```

### 自定义字体

1. 在`[博客根目录]/themes/butterfly/source/`新建文件夹`fonts`
将.tff字体文件放进去

2. 在`custom.css`中添加

    ```css
    @font-face {
      font-family: "字体名"; /* 字体名自定义即可 */
      src: url("/fonts/你的字体文件名.ttf"); /* 字体文件路径 */
      font-display: swap;
    }
    ```

3. 在`_config.butterfly.yml`中修改字体配置项

    ```yml
    # Global font settings
    # Don't modify the following settings unless you know how they work (非必要不要修改)
    font:
      global-font-size:
      code-font-size:
      font-family: "字体名"
      code-font-family:
    ```

------------------

## Ⅱ.插件安装

### Aplayer全局播放器

1. 安装`hexo-tag-aplayer`插件

    ```bash
    npm install hexo-tag-aplayer --save
    ```

2. 在`_config.yml`中新增配置项

    ```yml
    # APlayer
    # https://github.com/MoePlayer/hexo-tag-aplayer/blob/master/docs/README-zh_cn.md
    aplayer:
      meting: true
      asset_inject: false
    ```

3. 在`_config.butterfly.yml`中修改关于Aplayer配置项

    ```yml
    # Inject the css and script (aplayer/meting)
    aplayerInject:
      enable: true
      per_page: true
    ```

4. 在`custom.css`添加CSS样式使其自动缩进隐藏

    ```css
    .aplayer.aplayer-fixed.aplayer-narrow .aplayer-body {
      left: -66px !important;
      /* 默认情况下缩进左侧66px，只留一点箭头部分 */
    }

    .aplayer.aplayer-fixed.aplayer-narrow .aplayer-body:hover {
      left: 0 !important;
      /* 鼠标悬停是左侧缩进归零，完全显示按钮 */
    }
    ```

5. 在`_config.butterfly.yml`的`inject`配置项中添加Aplayer的容器

    ```yml
    inject:
      head:
      bottom:
        - <div class="aplayer no-destroy" data-id="5183531430" data-server="netease" data-type="playlist" data-fixed="true" data-mini="true" data-listFolded="false" data-order="random" data-preload="none" data-autoplay="false" muted></div>
    ```

    `data-id`：可填入歌单或歌曲id
    `data-server`：服务商，可选`netease`, `tencent`, `kugou`, `xiami`, `baidu`
    `data-type`：类型，可选`song`, `playlist`, `album`, `search`, `artist`

### 页脚添加时钟和github徽标

1. 安装`butterfly-footer-beautify`插件

    ```bash
    npm install hexo-butterfly-footer-beautify --save
    ```

2. 在`_config.yml`中新增配置项

    ```yml
    # footer_beautify
    # 页脚计时器：[Native JS Timer](https://akilar.top/posts/b941af/)
    # 页脚徽标：[Add Github Badge](https://akilar.top/posts/e87ad7f8/)
    footer_beautify:
      enable:
        timer: true # 计时器开关
        bdage: true # 徽标开关
      priority: 5 #过滤器优先权
      enable_page: all # 应用页面
      exclude: #屏蔽页面
        # - /posts/
        # - /about/
      layout: # 挂载容器类型
        type: id
        name: footer-wrap
        index: 0
      # 计时器部分配置项
      runtime_js: https://npm.elemecdn.com/hexo-butterfly-footer-beautify@1.0.0/lib/runtime.js
      runtime_css: https://npm.elemecdn.com/hexo-butterfly-footer-beautify@1.0.0/lib/runtime.css
      # 徽标部分配置项
      swiperpara: 3 #若非0，则开启轮播功能，每行徽标个数
      bdageitem:
        - link: https://hexo.io/ #徽标指向网站链接
          shields: https://img.shields.io/badge/Frame-Hexo-blue?style=flat&logo=hexo #徽标API
          message: 博客框架为Hexo_v5.4.0 #徽标提示语
        - link: https://butterfly.js.org/
          shields: https://img.shields.io/badge/Theme-Butterfly-6513df?style=flat&logo=bitdefender
          message: 主题版本Butterfly_v3.8.2
        - link: https://www.jsdelivr.com/
          shields: https://img.shields.io/badge/CDN-jsDelivr-orange?style=flat&logo=jsDelivr
          message: 本站使用JsDelivr为静态资源提供CDN加速
        - link: https://vercel.com/
          shields: https://img.shields.io/badge/Hosted-Vercel-brightgreen?style=flat&logo=Vercel
          message: 本站采用双线部署，默认线路托管于Vercel
        - link: https://vercel.com/
          shields: https://img.shields.io/badge/Hosted-Coding-0cedbe?style=flat&logo=Codio
          message: 本站采用双线部署，联通线路托管于Coding
        - link: https://github.com/
          shields: https://img.shields.io/badge/Source-Github-d021d6?style=flat&logo=GitHub
          message: 本站项目由Github托管
        - link: http://creativecommons.org/licenses/by-nc-sa/4.0/
          shields: https://img.shields.io/badge/Copyright-BY--NC--SA%204.0-d42328?style=flat&logo=Claris
          message: 本站采用知识共享署名-非商业性使用-相同方式共享4.0国际许可协议进行许可
      swiper_css: https://npm.elemecdn.com/hexo-butterfly-swiper/lib/swiper.min.css
      swiper_js: https://npm.elemecdn.com/hexo-butterfly-swiper/lib/swiper.min.js
      swiperbdage_init_js: https://npm.elemecdn.com/hexo-butterfly-footer-beautify/lib/swiperbdage_init.min.js
    ```

3. 可将`runtime_js`下载下来自行修改

### 侧栏添加时钟模块

1. 安装`butterfly-clock`插件

    ```bash
    npm install hexo-butterfly-clock --save
    ```

2. 在`_config.yml`中新增配置项

    ```yml
    # electric_clock
    # see https://akilar.top/posts/4e39cf4a/
    electric_clock:
      enable: true # 开关
      priority: 5 #过滤器优先权
      enable_page: all # 应用页面
      exclude:
        # - /posts/
        # - /about/
      layout: # 挂载容器类型
        type: class
        name: sticky_layout
        index: 0
      loading: https://npm.elemecdn.com/hexo-butterfly-clock/lib/loading.gif #加载动画自定义
      clock_css: https://npm.elemecdn.com/hexo-butterfly-clock/lib/clock.min.css
      clock_js: https://npm.elemecdn.com/hexo-butterfly-clock/lib/clock.min.js
      ip_api: https://pv.sohu.com/cityjson?ie=utf-8
    ```

### 添加gitcalendar模块

1. 安装`butterfly-clock`插件

    ```bash
    npm install hexo-filter-gitcalendar --save
    ```

2. 在`_config.yml`中新增配置项

    ```yml
    # hexo-filter-gitcalendar
    # see https://akilar.top/posts/1f9c68c9/
    gitcalendar:
      enable: true # 开关
      priority: 6 #过滤器优先权
      enable_page: / # 应用页面
      # butterfly挂载容器
      layout: # 挂载容器类型
        type: id
        name: recent-posts
        index: 0
      # volantis挂载容器
      # layout:
      #   type: class
      #   name: l_main
      #   index: 0
      # matery挂载容器
      # layout:
      #   type: id
      #   name: indexCard
      #   index: 0
      # mengd挂载容器
      # layout:
      #   type: class
      #   name: content
      #   index: 0
      user: sperte-s #git用户名
      apiurl: 'https://python-github-calendar-api.vercel.app'
      minheight:
        pc: 280px #桌面端最小高度
        mibile: 0px #移动端最小高度
      #color: "['#ebedf0', '#cdefec', '#a9e4de', '#1fc7b6', '#65cfc5', '#4dc8bb', '#39bbae', '#319d93', '#278178', '#216962', '#1b5852']"
      #color: "['rgb(145, 145, 145, 0.2)', '#c6ecc1', '#a0e2bb', '#1fc7b6', '#70c5d3', '#60a2ce', '#507ac9', '#4356c5', '#423cc4', '#5b3abc', '#7138b6']"
      #color: "['#e4dfd7', '#f9f4dc', '#f7e8aa', '#f7e8aa', '#f8df72', '#fcd217', '#fcc515', '#f28e16', '#fb8b05', '#d85916', '#f43e06']" #橘黄色调
      # color: "['#ebedf0', '#fdcdec', '#fc9bd9', '#fa6ac5', '#f838b2', '#f5089f', '#c4067e', '#92055e', '#540336', '#48022f', '#30021f']" #浅紫色调
      # color: "['#ebedf0', '#f0fff4', '#dcffe4', '#bef5cb', '#85e89d', '#34d058', '#28a745', '#22863a', '#176f2c', '#165c26', '#144620']" #翠绿色调
      color: "['#ebedf0', '#f1f8ff', '#dbedff', '#c8e1ff', '#79b8ff', '#2188ff', '#0366d6', '#005cc5', '#044289', '#032f62', '#05264c']" #天青色调
      container: .recent-post-item(style='width:100%;height:auto;padding:10px;') #父元素容器，需要使用pug语法
      gitcalendar_css: https://npm.elemecdn.com/hexo-filter-gitcalendar/lib/gitcalendar.css
      gitcalendar_js: https://npm.elemecdn.com/hexo-filter-gitcalendar/lib/gitcalendar.js
    ```

### 首页文章轮播

1. 安装`butterfly-swiper`插件

    ```bash
    npm install hexo-butterfly-swiper --save
    ```

2. 在`_config.yml`中新增配置项

    ```yml
    # hexo-butterfly-swiper
    # see https://akilar.top/posts/8e1264d1/
    swiper:
      enable: true # 开关
      priority: 5 #过滤器优先权
      enable_page: all # 应用页面
      timemode: date #date/updated
      layout: # 挂载容器类型
        type: id
        name: recent-posts
        index: 0
      default_descr: 再怎么看我也不知道怎么描述它的啦！
      swiper_css: https://npm.elemecdn.com/hexo-butterfly-swiper/lib/swiper.min.css #swiper css依赖
      swiper_js: https://npm.elemecdn.com/hexo-butterfly-swiper/lib/swiper.min.js #swiper js依赖
      custom_css: https://npm.elemecdn.com/hexo-butterfly-swiper/lib/swiperstyle.css # 适配主题样式补丁
      custom_js: https://npm.elemecdn.com/hexo-butterfly-swiper/lib/swiper_init.js # swiper初始化方法
    ```

3. 使用方法

    在文章的`front_matter`中添加`swiper_index`配置项即可

    ```markdown
    ---
    title: 文章标题
    date: 创建日期
    updated: 更新日期
    cover: 文章封面
    description: 文章描述
    swiper_index: 1 #置顶轮播图顺序，非负整数，数字越大越靠前
    ---
    ```

------------------

## 后言

魔改一时爽，一直魔改一直爽。

------------------

{% hideToggle 文章参考,#A4D8FA%}
[主题美化日记 | 糖果屋](https://akilar.top/posts/f99b208/)
[Hexo博客之butterfly主题优雅更换背景 | 小康博客](https://www.antmoe.com/posts/7198453/)
{% endhideToggle %}
