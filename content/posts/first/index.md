+++
title = 'First'
description = "This is the first page (a test page) for my blog."
date = 2024-09-07T20:11:34+05:30
# author = "prabhpreet singh"
draft = true
# summary = "this is a summary"
weight = 1
aliases = ["/first"]
tags = ["first", "test"]
showToc = true
TocOpen = false
hidemeta = false
comments = false
canonicalURL = "https://canonical.url/to/page"
disableHLJS = true # to disable highlightjs
disableShare = false
hideSummary = false
searchHidden = false
ShowReadingTime = true
ShowBreadCrumbs = true
ShowPostNavLinks = true
ShowWordCount = true
ShowRssButtonInSectionTermList = true
UseHugoToc = true
+++
<!-- [[cover]]
    image = "<image path/url>" # image path/url
    alt = "<alt text>" # alt text
    caption = "<text>" # display caption under cover
    relative = false # when using page bundles set this to true
    hidden = true # only hide on current single page -->



## sub heading
[link]({{< relref "/about#About me:" >}})

some text

<!--more-->

^^ for summary


https://gohugo.io/content-management/cross-references/

1. point 1
2. point 2

<!-- ,hl_lines=[2,"5-7"],linenostart=199 -->
```python  {linenos=table,linenostart=199}
print("hello")
print("hello")
print("hello")
for i in range(100):
    print("world")
print("hello")
@dataclass
class Data:
    pass
print("hello")
print("hello")
print("hello")
```

### another heading
- some more point
- and another

{{< highlight python "linenos=table,hl_lines=[2,"5-7"],linenostart=199" >}}
print("hello")
print("hello")
print("hello")
print("hello")
print("hello")
print("hello")
print("hello")
{{< / highlight >}}
#### another heading 2


https://stackoverflow.com/questions/71501256/how-to-insert-an-image-in-my-post-on-hugo

![some image](/static/images/favicon.png)
![another image](./favicon.png)

https://gohugo.io/content-management/image-processing/
<!-- {{ $image1 := resources.Get "images/favicon.png" }} -->
<!-- <img src="{{ $image1.RelPermalink }}" width="{{ $image1.Width }}" height="{{ $image1.Height }}"> -->

<!-- {{ $image2 := .Resources.Get "favicon.png" }} -->
<!-- <img src="{{ $image2.RelPermalink }}" width="{{ $image2.Width }}" height="{{ $image2.Height }}">  -->

<!-- <figure class="image is-3by2">
  <img alt="Yellow Duck" src="{{ $image2 }}" />
</figure>
 -->

<!-- {{ $u := "https://gohugo.io/img/hugo-logo.png" }}
{{ with resources.GetRemote $u }}
  {{ with .Err }}
    {{ errorf "%s" . }}
  {{ else }}
    <img src="{{ .RelPermalink }}" width="{{ .Width }}" height="{{ .Height }}">
  {{ end }}
{{ else }}
  {{ errorf "Unable to get remote resource %q" $u }}
{{ end }} -->