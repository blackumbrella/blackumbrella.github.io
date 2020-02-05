---
title: Gitbook生成PDF字体不正确的问题及解决方案
date: 2020-02-04 17:35:57
tags: gitbook, pdf
---

采用gitbook pdf转换中文markdown 文件到PDF时发现部分字符加粗显示，部分显示正常，但是无法辨识正确的系统字体。
最终发现解决办法为：

1. 增加book.json文件到文件夹的根目录（可参考默认文件作为模板）
2. 增加以下element到json文件：
    ```js
    "pdf": {
      "pageNumbers": true,
      "fontSize": 12,
      "paperSize": "a4",
      "fontFamily":"Microsoft YaHei",
      "margin": {
        "right": 30,
        "left": 30,
        "top": 30,
        "bottom": 50
      }
    }
   ```
   其中fontFamily最为重要，同样的中文字体，例如雅黑，fontFamily可以是 `Microsoft YaHei`,也可以是中文的`微软雅黑`。推荐采用英文。

3. 执行 `gitbook pdf . ./target.pdf`
