---
alias: Academic Website
year: 2023.06.12
sort: Windows
nation: Chinese
crew: 
rate: 
info: Hugo
date: 2023-06-12-Monday 15:33:19
update: 2023-07-19-Wednesday 18:28:21
tags: [read/year2023, read/month06]
id: read20230612153319
---
---

# 1 Prerequisites

## 1.1 Domain Name

- [阿里云域名部署到netlify静态服务器教程](https://jingyan.baidu.com/article/3c343ff73872d54c3679632c.html)
- [阿里云官网](https://cn.aliyun.com/)
- [wujiming.com](https://www.wujiming.com)
- [域名管理-修改DNS](https://dc.console.aliyun.com/next/index?spm=5176.12818093.console-base.ddomain.29b916d0qKzdGB#/domain-list/all)
---

## 1.2 Hugo Academic/Wowchemy

### 1.2.1 Scoop Installation

1. Set PowerShell execution policy

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

2. Typical Installation

```
irm get.scoop.sh | iex
# You can use proxies if you have network trouble in accessing GitHub, e.g.
irm get.scoop.sh -Proxy 'http://<ip:port>' | iex
```

3. **Run the command as administrator**

```
iex "& {$(irm get.scoop.sh)} -RunAsAdmin"
```

4. **Scoop config**

```
	 "last_update":  "2023-05-18T14:28:06.3210175+08:00",
    "Proxy":  "127.0.0.1:7890",
    "aria2-enabled":  "ture",
    "scoop_branch":  "master",
    "scoop_repo":  "https://github.com/ScoopInstaller/Scoop"
```


- [Scoop installer - GitHub](https://github.com/ScoopInstaller/Install)

- [Installing scoop fails: "Running the installer as administrator is disabled by default - Stack Overflow](https://stackoverflow.com/questions/74763204/installing-scoop-fails-running-the-installer-as-administrator-is-disabled-by-d)
---

### 1.2.2 Hugo Extended Installation and It's Prerequisites


```
scoop install git go hugo-extended nodejs

```


1. Hugo-extended

```
scoop install hugo-extended
```

`scoop config edit`


2. Prerequisites
   1. Go
      [All releases - The Go Programming Language](https://go.dev/dl/)
   2. Git
       [Installing Git](https://git-scm.com/download/win)
   3. Hugo
      - Run the command : 
        `go install -tags extended github.com/gohugoio/hugo@latest hugo version`
      - Download manually :
        [Release v0.111.3 · gohugoio/hugo · GitHub](https://github.com/gohugoio/hugo/releases/tag/v0.111.3)

- [Windows | Hugo tutorial](https://gohugo.io/installation/windows/)

   4. NodeJS
      - `scoop install nodejs`, `node -v`, `npm -v
      - [Node.js](https://nodejs.org/en)
`
- [Wowchemy - Docs](https://wowchemy.com/docs/getting-started/install-hugo-extended/)
---


---

## 1.3 Github



---

## 1.4 Netlify



---


# 2 Building Academic Website
## 1
### 1
### 2
### 3

---

## 2 Build Site on Your Pc
### 1 Build Site with the Latest Version of Hugo-academic
1. Locate the repository, and either download the ZIP or use [Git clone](https://github.com/wowchemy/starter-academic.git) to download it from [starter-hugo-academic](https://github.com/wowchemy/starter-hugo-academic).
   ![[Pasted image 20230523214847.png]]
2. Remove the 'main' suffix.
   ![[Pasted image 20230523215254.png]]
3. Use the command `cd E:\WuJiming\My-website\starter-hugo-academic`.
4. Set the proxy.
   `$Env:http_proxy="http://127.0.0.1:7890"`
   `$Env:https_proxy="http://127.0.0.1:7890"`.
5. `hugo server`
   `http://localhost:1313/`.

### 2 Build Site with an Old Version of Hugo-academic
1. `cd E:\WuJiming\My-website\Hugo-academic-old`.
2. `hugo new site my-academic-site`.
3. Download the `wowchemy-hugo-themes-4.7.0` theme from [starter-hugo-academic](https://github.com/wowchemy/starter-hugo-academic).
4. Remove the 'main' suffix.
5. copy the `wowchemy-hugo-themes-4.7.0` folder to replace and paste `E:\WuJiming\My-website\Hugo-academic-old\my-academic-site\themes`.
6. copy `examplesite`  subfolder to replace and paste `E:\WuJiming\My-website\Hugo-academic-old\my-academic-site`.
7. Set the proxy.
   `$Env:http_proxy="http://127.0.0.1:7890"`
   `$Env:https_proxy="http://127.0.0.1:7890"`
8. `hugo server`
   `http://localhost:1313/`.

### 3 Some Common Problems
1. hugo server
   `Error: failed to download modules: binary with name "go" not found`
   `Solution: set system environmental variable D:\go\bin`


---

## 3. Edit Your Site on Your Pc
### 1.
[See all icons](https://wowchemy.com/docs/getting-started/page-builder/#icons)

### 2.


### 3.


---


# 3 Improve the Academic Website




---

about.biography
![[Pasted image 20230523201139.png]]


# Appendix
 - # [Teaching video](https://www.bilibili.com/video/BV1Gz4y1f7Qj/?spm_id_from=333.337.search-card.all.click&vd_source=4f4f9eaa7c3c2df88a108df3464284bc)
 - # [Jiming Wu's Website](https://jimingwu.netlify.app)
- # [Jiming Wu's website overview with netlify](https://app.netlify.com/teams/spongebaby1/overview?_ga=2.78038996.1544300514.1680356470-1317506125.1679836976)
- # [Hugo.io Docs](https://gohugo.io/documentation/)
- # [Wowchemy Templates](https://wowchemy.com/templates/)
- # [Wowchemy Docs](https://wowchemy.com/docs/)
- # [Wowchemy Disorder](https://discord.com/channels/722225264733716590/742892432458252370)
- # []()
- # [Examples](https://example.com)
	- # [UBC Fariborz Taghipour](https://chbe.ubc.ca/fariborz-taghipour/)
	- # [UBC Mahyar Mohaghegh Montazeri](https://www.mahyarmmontazeri.com/)
	- # [Simon J. kiss](https://sjkiss.github.io/)
	- [曲延云-厦门大学](https://quyanyun.xmu.edu.cn/index.htm)
