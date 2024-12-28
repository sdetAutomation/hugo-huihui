---
layout:     post
title:      "Life of The Hui"
subtitle:   "Read all about HuiHui!"
date:       2024-12-27
author:     "The Hui's Dad"
image:      "https://img.zhaohuabing.com/post-bg-2015.jpg"
---

# Huihui's Adventures


In the morning sun with fur so fine, Huihui wakes with a sparkle that shines. Salt and pepper, a coat so grand, Mini schnauzer with a gentle hand.Bounding through fields with joyous glee, Huihui chases butterflies free. With each wag of his tiny tail, He brings delight, without fail. In cozy nooks, he curls up tight, Dreaming of adventures in the night. Guarding his home with courage true, Huihui's heart is strong and blue. With eyes that twinkle, bright and keen, He's the cutest pup you've ever seen. A loyal friend, a playful sprite, Huihui makes the world just right. Oh, Huihui, with your loving bark, You light the way even in the dark. Salt and pepper, full of cheer, You're the best friend, oh so dear.

# Huihui's Journey

清晨阳光下，毛发银灰， Huihui苏醒，精神抖擞最可爱。 路在脚下，心向远方， 小小雪纳瑞，梦想无限长。
欢快奔跑在宽广草地， Huihui追逐蝴蝶，心中充满欢喜。 每一次摇尾巴的瞬间， 欢乐洋溢，温暖蔓延。
温暖角落里，蜷缩得紧， 夜晚冒险的梦，心灵的指引。 勇敢守护家园，无畏坚定， Huihui的心灵，像蓝天纯净。
明亮眼眸，机敏炯炯， 他是世间最可爱的小宠。 忠诚朋友，淘气精灵， Huihui让世界变得温馨。
哦，Huihui，你温暖的汪声， 照亮了黑暗中的道路与人生。 路在脚下，心向远方， 盐与胡椒，充满了欢畅。

## Screenshots

**Home**
![screenshot](/img/fullscreenshot.png)

**Post**
![screenshot](/img/post.png)

**Search**
![screenshot](/img/sitesearch.png)

**Disqus**
![screenshot](/img/disqus.png)

**Wechat Pay & Alipay**
![screenshot](/img/rewards.png)

## Quick Start
Go to the directory where you have your Hugo site and run:

```
$ mkdir themes
$ cd themes
$ git clone https://github.com/zhaohuabing/hugo-theme-cleanwhite.git
```

If your site is already a git project, you may want to choose to add the cleanwhite theme as a submodule to avoid messing up your existing git repository.

```
$ mkdir themes
$ git submodule add https://github.com/zhaohuabing/hugo-theme-cleanwhite.git themes/hugo-theme-cleanwhite
```
Run  Hugo Build-in Server Locally

```
$ hugo serve -t  hugo-theme-cleanwhite
```
Now enter [`localhost:1313`](http://localhost:1313) in the address bar of your browser.

If you start from scratch, there is a working Hugo site configured with the CleanWhite theme in the [exampleSite](https://github.com/zhaohuabing/hugo-theme-cleanwhite/tree/master/exampleSite) directory.  You can use it as a starting point for your site.

For more information read the official [setup guide](https://gohugo.io/overview/installing/) of Hugo 

## Configuration
First, let's take a look at the [config.toml](https://github.com/zhaohuabing/hugo-cleanwhite-theme/tree/master/exampleSite/config.toml). It will be useful to learn how to customize your site. Feel free to play around with the settings.

### Comments
The optional comments system is powered by [Disqus](https://disqus.com). If you want to enable comments, create an account in Disqus and write down your shortname.

```toml
disqusShortname = "your-disqus-short-name"
```
You can disable the comments system by leaving the `disqusShortname` empty.

### Disqus in China
Disqus is inaccessible in China. To get it to work, we can set up a proxy with [disqus-php-api](https://github.com/zhaohuabing/disqus-php-api) in a host which sets between the client browser and the Disqus server. The idea is that if Disqus can be reached in the guest network, the blog page will show the original Disqus comments UI, otherwise, it will downgrade and use the proxy to access the Disqus, the UI will be a little different, but the visitors can still write their comments on the page.

The client side java script has already been integrated to CleanWhite them, but you need to set up a proxy server yourself.

The proxy is written in php, which can be found here: https://github.com/zhaohuabing/disqus-php-api/tree/master/api

You need to specify  your Disqus account information in the config.php.
```
define('PUBLIC_KEY', '');
define('SECRET_KEY', '');
define('DISQUS_USERNAME', '');
define('DISQUS_EMAIL', '');
define('DISQUS_PASSWORD', '');
define('DISQUS_WEBSITE', '');
define('DISQUS_SHORTNAME', '');
```
Set the proxy server address in the site config file of your Hugo project.
```toml
disqus_proxy = "http://yourdisqusproxy.com"
```
### Site Search with Algolia
Follow this [tutorial](https://forestry.io/blog/search-with-algolia-in-hugo/#3-create-your-index-in-algolia) to create your index in Algolia. The index is just the storage of the indexing data of your site in the the cloud . The search page of CleanWhite theme will utilize this indexing data to do the search.

Go to the directory where you have your Hugo site and run the following commands:
```bash
$ npm init
$ npm install atomic-algolia --save
```
Next, open up the newly created package.json, where we’ll add an NPM script to update your index at Algolia. Find "scripts", and add the following:
```josn
"algolia": "atomic-algolia"
```
Algolia index output format has already been supported by the CleanWhite theme, so you can just build your site, then you’ll find a file called algolia.json in the root, which we can use to update your index in Algolia.
Generate index file:
```bash
$ hugo
```
Create a new file in the root of your Hugo project called .env, and add the following contents:
```bash
ALGOLIA_APP_ID={{ YOUR_APP_ID }}
ALGOLIA_ADMIN_KEY={{ YOUR_ADMIN_KEY }}
ALGOLIA_INDEX_NAME={{ YOUR_INDEX_NAME }}
ALGOLIA_INDEX_FILE={{ PATH/TO/algolia.json }}
```
Now you can push your index to Algolia by simply running:
```bash
$ npm run algolia
```
Add the following variables to your hugo site config so the search page can get access to algolia index data in the cloud:
 ```
algolia_search = true
algolia_appId = {{ YOUR_APP_ID }}
algolia_indexName = {{ YOUR_INDEX_NAME }}
algolia_apiKey = {{ YOUR_SEARCH_ONLY_KEY }}
```
Open search page in your browser: http://localhost:1313/search

### Analytics

You can optionally enable Google or Baidu Analytics. Type your tracking code in the 

```toml
googleAnalytics = "G-XXXXX"
ba_track_id  = "XXXXXXXXXXXXXXXX"
```
Leave the `googleAnalytics`  or 'ba_track_id ' key empty to disable it.

### Wechat Pay & Alipay Rewards

You can enable Wechat Pay & Alipay to allow readers send you money. So if they like your articles, you may even get rewards from your writing. Now you must be motivated to write more.

* Enable Wechat Pay & Alipay in the site config
```toml
reward = true
```
* Replace the QR codes of Wechat Pay & Alipay by overriding the photos in folder /static/img/reward/, otherwise the money will be sent to my accounts!


## Thank
Thanks for the great jobs of [huxblog Jekyll Theme](https://github.com/Huxpro/huxpro.github.io) and [Clean Blog Jekyll Theme](https://github.com/BlackrockDigital/startbootstrap-clean-blog-jekyll) which are the the two upstream projects CleanWhite Hugo theme is based on.

## Feedback
If you find any problems, please feel free to [raise an issue](https://github.com/zhaohuabing/hugo-theme-cleanwhite/issues/new) or create a pull request to fix it. 

If it's helpful for you, I would appreciate it if you could star this repository, thanks!

