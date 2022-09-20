---
layout: docs
title: Docker publish
published: 2022-09-19
Author: Kevin Frey
add toc: false
add sidebar: _sidebars\mainSidebar.md
---

Start docker then use: 

```bash 
.\build.cmd docker-publish
```

This will ask you if you have the correct **version** and will ask you to **test the image** before publishing. After testing the image, you can `Ctrl + c` the console and you will be asked if the image works alright and if you want to publish.

__OR__

<details><summary>Step by step</summary>
<p>

1. Create image 
```bash
docker build -t swate -f build/Dockerfile.publish .
```

2. Test image 
```bash
docker run -it -p 8085:8085 swate
```

3. Create tag for image
```bash
docker tag swate:latest freymaurer/swate:X.X.X
docker tag swate:latest freymaurer/swate:latest
```

Remember to replace "X.X.X" with the correct next SemVer version.

4. Push the image
```bash
docker push freymaurer/swate:X.X.X
docker push freymaurer/swate:latest
```

</p>
</details>