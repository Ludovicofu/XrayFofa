# XrayFofa
🎉🎉🎉
一款将xray和fofa结合运行的脚本,配置方法参考了piaolin大佬写的<a href="https://github.com/piaolin/fofa2Xray">fofa2Xray</a>
增加了一些自己的想法(望指正),点个小星星支持一下吧🌹🌹🌹

XrayFofa git克隆下载:git clone https://github.com/Miagz/XrayFofa.git 
<br>
克隆下载需安装第三方库:  python3 -m pip install requests pyyaml lxml
<br>

# 注意
fofa爬虫功能用不了了! fofa开了反爬虫!

# 更新
## 1.4.0
* 修复了普通会员启动时出bug（fofa普通会员只能API查询数据100条的硬性规定我是真的无能为力，只能提醒一下一下啦）
* 增加了xray plugins的自定义模式，可以随意自定义自己需要的plugins

## 1.3.0
* 修复了fofa API 调用问题(应该没啥问题了)
* 对代码进行了简单的优化,fofa API 连不上时不会出现 报错一堆的情况了
## 1.2.0
* 更新 fofareptile 功能,使用python爬虫爬取fofa搜索结果,利用fofa关键字查询特性进行绕过注册会员只能看五页的限制,推荐fofa注册会员使用
* 新增windows版xray的调用
## 1.1.0
* 新增python第三方包
* 修复了xray扫描结果无法输出问题

# scan_config.yaml
  ~~~yaml
#xray配置
xray:
        #扫描结果存储路径
        file_path: 
        
        #xray文件位置,不填则为XrayFofa根目录,例如:/路径/xray_***_amd64
        xray_file_path:
        
        #xray 结果输出方式默认是 html|xray输入出方式仅有html,json,text
        input_file_type: 

        #自定义xray的plugins 默认为：xss,dirscan,xxe,upload,jsonp,brute-force,cmd-injection,crlf-injection,phantasm,sqldet
        xray_plugins:

#fofa配置
fofa:
        #fofa cookie
        Fofa_Cookie: 

        #fofa登录邮箱
        Fofa_email: 

        #fofa key值
        Fofa_key: 

        #fofa搜索语法,可直接在后面添加
        fofaQuerysyntax:
                - status_code=200


#全局配置
global:
        #是否开启fofa爬虫模式,开启后需填写Fofa_Cookie和fofaQuery(开启后将不会使用fofaAPI,fofa普通会员以及fofa高级会员勿用)
        fofareptile: no
        
        #是否只扫描域名,如果需要请修改为yes
        scan_domain_name: no

        #多线程数量
        threads: 5
        

 ~~~
### xray配置 ✔
> input_file_type 
<p>xray输出方式 为空的话则默认为html格式输出</p>

> file_path 
<p>xray结果的输出位置,为空则默认在当前目录下生成一个以 input_file_type 中所填写的输出方式作为名称</p>

> xray_file_path
<p>xray所在的路径(包含xray文件名) 不填则为XrayFofa根目录,例如:/路径/xray_***_amd64</p>

> xray_plugins
<p>自定义xray的plugins 默认为：phantasm,brute_force,sqldet,cmd_injection</p>

### fofa配置 ✔
> Fofa_Cookie
<p>fofa用户cookie,fofareptile启动后才会调用,留空后则爬虫爬取时每次只爬取一页</p>

> Fofa_email
<p>fofa登录邮箱</p>

> Fofa_key
<p>fofa api key 可在fofa个人资料中查看</p>
 
> fofaQuerysyntax
<p>fofa查询语法 跟fofa使用差不多 更多搜索语法可在后面追加</p>

  ~~~
  fofaQuerysyntax:
          - status_code=200
          - country="CN"
          - title="后台管理系统"
  ~~~

### 全局配置 ✔
> fofareptile
<p>使用python爬虫爬取fofa搜索结果,利用fofa关键字查询特性进行绕过注册会员只能看五页的限制,推荐fofa注册会员使用</p>
<p>fofareptile启动后,需填写Fofa_Cookie选项</p>
<p>## 缺陷 ## :由于使用随机组合关键字查询,会出现查询不到的结果,所以启动会比较慢(后续会努力完善)</p>

> scan_domain_name
<p>开启后xray只会扫描fofa扫描出的域名,ip直接过滤 默认为关闭状态</p>

> threads
<p>多线程大小</p>

# demo
<img src="https://github.com/Miagz/image/blob/master/pm.gif">
