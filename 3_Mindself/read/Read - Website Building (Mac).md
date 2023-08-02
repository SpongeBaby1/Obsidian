---
alias: Academic Website
year: 2023.06.12
sort: Mac
nation: Chinese
crew: 1st
rate: 1st
info: Hugo
date: 2023-06-12-Monday 15:51:59
update: 2023-08-03-Thursday 00:11:59
tags: [read/year2023, read/month06]
id: read20230612155159
---
---

# 1 Prerequisites

## 1.1 Domain Name

- [阿里云域名部署到netlify静态服务器教程](https://jingyan.baidu.com/article/3c343ff73872d54c3679632c.html)
- [阿里云官网](https://cn.aliyun.com/)
- [wujiming.com](https://www.wujiming.com)
- [域名管理-修改DNS](https://dc.console.aliyun.com/next/index?spm=5176.12818093.console-base.ddomain.29b916d0qKzdGB#/domain-list/all)
---

## 1.2 Hugo Extended

- Home brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

- Git golang hugo node
```
brew install git golang hugo node
```
---

## 1.3 Visual Studio Code

- install Visual Studio Code
```
brew install visual-studio-code
```

- config vscode 
[05 VS Code的安装\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1m4411c7ia?p=5&vd_source=4f4f9eaa7c3c2df88a108df3464284bc)

---


# 2 Edit on Your Pc


## [Block view](https://wowchemy.com/docs/getting-started/page-builder/)
- List (1)
- Compact (2)
- Card (3)
- Citation (4)
    - For classic APA or MLA styled publication lists
    - Optionally, edit the value of `citation_style` in `params.yaml` to APA or MLA
- Showcase (5)
- Masonry
    - Intended for use with the Portfolio widget to provide a Pinterest-style layout
- Or, **create your own view** in `layouts/partials/views/community/<name>.html` (creating the folders) and reference it as `view: community/<name>` where `<name>` is a unique name for your view (with no spaces in the name)
    - take a look at the [code for the built-in views](https://github.com/wowchemy/wowchemy-hugo-themes/tree/main/modules/wowchemy/layouts/partials/views) for inspiration
    - consider sharing your new view with the Community on Discord, or publishing it as a Hugo Module.



## [Customise the site header](https://wowchemy.com/docs/getting-started/customization/)
`header:
  navbar:
# Choose a Navigation Block
    block: navbar
# Display the Navigation Bar?
    enable: true
# Align Menu Links: Left (l), Center (c), or Right (r)
    align: l
# Display Your Site Title or `assets/media/logo*` Image in the Nav Bar?
    show_logo: true
# Show a Language Chooser (if You Have Translated Your Site content)?
    show_translations: true
# If `show_translations` is Enabled, Do You Wish to Display the Current Language Name?
    show_language: false
# Let the User Override the Default light/dark Mode of Your Theme?
    show_day_night: true
# Let the User Search From the Nav Bar?
    show_search: true
# Attempt to Automatically Highlight the Active Menu Link? Can Be Disabled for Complex Sites.
    highlight_active_link: true`


## 2.1 Biography


---

## 2.2 Publications




---



# 3 [Troubleshooting](https://wowchemy.com/docs/hugo-tutorials/troubleshooting/#error-file-not-found-or-failed-to-extract)

1. `Error: failed to resolve output format`
Cause 1: Hugo’s Cache
	(A) Manually **delete Hugo’s default cache folder** and re-run Hugo. Hugo’s cache folder defaults to `$TMPDIR/hugo_cache/` (just run  `echo $TMPDIR\` or `open $TMPDIR/hugo_cache/` in terminal) on Mac/Linux and `%TMP%\hugo_cache\` on Windows.
	or (B) **Set a custom Hugo cache folder when you run Hugo**, for example: `hugo server --cacheDir ./cache/` where `./cache/` is the path of a temporary folder to create. Then you can easily locate and delete Hugo’s cache folder should you experience this issue.
	
Cause 2: Missing Hugo Module

2. 


# Appendix

[01 Academic主题介绍\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1iA411v7Gi?p=2&vd_source=4f4f9eaa7c3c2df88a108df3464284bc)
[Wowchemy开源网站搭建器](https://wowchemy.com/)
[Quickstart your Hugo website with this Hugo tutorial](https://wowchemy.com/docs/getting-started/install-hugo-extended/)

[Discord](https://discord.com/channels/722225264733716590/738922126966521907)
[Mahyar Mohaghegh Montazeri](https://www.mahyarmmontazeri.com/)
[Simon J. Kiss](https://sjkiss.github.io/)
[Thomas W. Price | HINTS Lab](https://isnap.csc.ncsu.edu/home/public/authors/thomas-w-price/)
[HINTS Lab](https://isnap.csc.ncsu.edu/home/public/)
[Bijan Mazaheri](https://bijanmazaheri.com/)