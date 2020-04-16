---
description: ブラウザを指定する方法
---

# Jupyter Notebook

```bash
$ jupyter notebook --generate-config
```

で生成された ~/.jupyter/jupyter\_application\_config.py を編集。

```python
import webbrowser
webbrowser.register('chrome', None, webbrowser.GenericBrowser('C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe'))
c.NotebookApp.browser = 'chrome'
```

```python
import webbrowser
webbrowser.register('firefox', None, webbrowser.GenericBrowser('C:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe'))
c.NotebookApp.browser = 'firefox'
```

