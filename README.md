# document
项目文档，代码网址另附在文件里

## 项目报告/个人小结
在 report 文件夹里
命名方式 学号_姓名_项目小结.md

## 前端
项目网址在如下，readme等文档也在项目中

https://github.com/Drice27149/frontend

## 服务端
同前端，项目网址如下，readme等文档也在项目中

https://github.com/chenguofan1999/TBD_API

## API设计
如下网址

https://app.swaggerhub.com/apis-docs/chenguofan1999/TBD/1.0.0

----
# 项目说明
## 前后端分离的开发实战

## 像每个网站的 web 服务端项目: TBD API

本项目的服务端提供者默认客户端开发者**还没想好要做什么**，因此提供了大部分网站共有的资源要素，做出了一个可以成为任何网站的 web 服务端项目 —— TBD API。

[TBD API](https://app.swaggerhub.com/apis-docs/chenguofan1999/TBD/1.0.0#)

TBD API 提供了：

1. 几乎每个网站都有的用户服务，包括
    1. 几乎每个网站都有的用户注册和登录服务
    3. 几乎每个网站都有的用户信息管理服务
2. 几乎每个网站都有的内容管理服务，TBD API 提供了模糊的资源类型 **Content** ，你可以将它实现为任何东西
    1. 喜欢长内容？您可以把它实现成博客
    2. 喜欢短内容？您可以把它实现成推特
    3. 主打图文？内容管理服务提供了图片接口，您可以把它实现成微信朋友圈
    4. 只想要图片？您总是可以只取 Content 的一个子集，把它实现成 Instagram !
3. 几乎每个网站都有的评论管理服务
    1. 喜欢微信式的扁平单层评论区？TBD API 提供了全部评论的接口
    2. 喜欢大部分网络社区的两层评论区？TBD API 提供了查询回复的接口
    3. 喜欢推特式的不一样的链式评论？TBD API 的评论结构天然成链，能轻松实现
4. 其他几乎每个网站都有的服务
    1. 收藏喜欢功能
    2. 用户关注
    3. 公共内容推送


### 部署

1. 我已将 API 部署至云服务器，基址为 http://159.75.1.231:5005 , 推荐直接使用。
2. 您也可以在自己的电脑上部署，拉取 [服务端仓库](https://github.com/chenguofan1999/TBD_API) 到您的个人电脑上，需要配置好 MYSQL，将您的 MYSQL 认证信息填入 `model/connect.go` 中，执行 `go run tbd.go` 即可。

### API 示例

**curl**

- 示例1
    ```
    $ curl -i http://159.75.1.231:5005/contents\?type\=public\&page\=1\&perPage\=3
    HTTP/1.1 200 OK
    Access-Control-Allow-Headers: Content-Type, Authorization
    Access-Control-Allow-Methods: POST, OPTIONS, GET, PUT, DELETE
    Access-Control-Allow-Origin: *
    Access-Control-Expose-Headers: Access-Control-Allow-Origin
    Content-Type: application/json; charset=utf-8
    Date: Mon, 21 Dec 2020 04:27:42 GMT
    Content-Length: 699

    [{"contentID":190,"title":"IAMHAPE","text":"以form-data方式填入","createTime":1608513964,"author":{"username":"Tom","bio":"A SE student","avatar":"static/avatars/wogbgzrirnbtufgipfuh.png"},"images":["static/images/xbabdldprepicsinacld.png"]},{"contentID":189,"title":"IAMHAPE","text":"以form-data方式填入","createTime":1608513962,"author":{"username":"Tom","bio":"A SE student","avatar":"static/avatars/wogbgzrirnbtufgipfuh.png"},"images":["static/images/rafyqhxuwvasnojfimnc.png"]},{"contentID":188,"title":"IAMHAPE","text":"以form-data方式填入","createTime":1608513949,"author":{"username":"Tom","bio":"A SE student","avatar":"static/avatars/wogbgzrirnbtufgipfuh.png"},"images":[]}]%
    ```


- 示例2
    ```
    $ curl -i http://159.75.1.231:5005
    HTTP/1.1 200 OK
    Access-Control-Allow-Headers: Content-Type, Authorization
    Access-Control-Allow-Methods: POST, OPTIONS, GET, PUT, DELETE
    Access-Control-Allow-Origin: *
    Access-Control-Expose-Headers: Access-Control-Allow-Origin
    Content-Type: application/json; charset=utf-8
    Date: Mon, 21 Dec 2020 04:37:12 GMT
    Content-Length: 472

    {"comment_url":"http://159.75.1.231:5005/comments/{commentID}","comments_url":"http://159.75.1.231:5005/comments","content_url":"http://159.75.1.231:5005/content/{contentID}","contents_url":"http://159.75.1.231:5005/contents","current_user_url":"http://159.75.1.231:5005/user","followers_url":"http://159.75.1.231:5005/users/{username}/followers","following_url":"http://159.75.1.231:5005/users/{username}/followint","user_url":"http://159.75.1.231:5005/users/{username}"}
    ```

**postman**

- 示例1:

    GET http://159.75.1.231:5005/contents?type=public&page=1&perPage=3

    ```
    [
        {
            "contentID": 190,
            "title": "IAMHAPE",
            "text": "以form-data方式填入",
            "createTime": 1608513964,
            "author": {
                "username": "Tom",
                "bio": "A SE student",
                "avatar": "static/avatars/wogbgzrirnbtufgipfuh.png"
            },
            "images": [
                "static/images/xbabdldprepicsinacld.png"
            ]
        },
        {
            "contentID": 189,
            "title": "IAMHAPE",
            "text": "以form-data方式填入",
            "createTime": 1608513962,
            "author": {
                "username": "Tom",
                "bio": "A SE student",
                "avatar": "static/avatars/wogbgzrirnbtufgipfuh.png"
            },
            "images": [
                "static/images/rafyqhxuwvasnojfimnc.png"
            ]
        },
        {
            "contentID": 188,
            "title": "IAMHAPE",
            "text": "以form-data方式填入",
            "createTime": 1608513949,
            "author": {
                "username": "Tom",
                "bio": "A SE student",
                "avatar": "static/avatars/wogbgzrirnbtufgipfuh.png"
            },
            "images": []
        }
    ]
    ```

- 示例2： 

    GET http://159.75.1.231:5005

    ```
    {
        "comment_url": "http://159.75.1.231:5005/comments/{commentID}",
        "comments_url": "http://159.75.1.231:5005/comments",
        "content_url": "http://159.75.1.231:5005/content/{contentID}",
        "contents_url": "http://159.75.1.231:5005/contents",
        "current_user_url": "http://159.75.1.231:5005/user",
        "followers_url": "http://159.75.1.231:5005/users/{username}/followers",
        "following_url": "http://159.75.1.231:5005/users/{username}/followint",
        "user_url": "http://159.75.1.231:5005/users/{username}"
    }
    ```

### 要求满足情况

|要求|满足情况|
|---|---|
|资源类型不能少于 4 个|满足，user/content/comment/follow/like|
|数据来源必须真实|满足，真实手打录入|
|服务器端数据库支持|Mysql|
|API root 能获取简单 API 服务列表|支持，如示例2|
|支持分页|支持，如示例1|
|支持Token认证|所有需要登录的API都支持且必须Token认证|