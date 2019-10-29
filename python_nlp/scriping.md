# Scriping

Using library Selenium

```bash
$pip install selenium
$pip install chromedriver_binary
```

```python
from selenium import webdriver
import chromedriver_binary

driver = webdriver.Chrome()
driver.get('http://www.google.com/')
time.sleep(2)
serch_box = driver.find_element_by_name('q')#find the input box
serch_box.send_keys('ChromeDriver')#send something
serch_box.submit()#?
time.sleep(2)
driver.quit()
```

```python
#ある要素を取得したいとき
#serch by name
driver.find_element_by_name()
#serch by class
driver.find_element_by_class_name()
#serch by path
driver.find_element_by_xpath("//*[@id='xxx']")
#Elementもしくは、id, nameの指定が可能
#属性を取得したいとき
driver.find_element_by_XXXX.get_attribute("value")
```

```python
#ページの遷移
driver.get("URL")
#一つ前に戻りたいとき
driver.back()
#一つ前に進みたいとき
driver.forward()
#ブラウザを更新する
driver.refresh()
#現在のURLを知りたいとき
driver.current_url
#タイトルを知りたいとき
driver.title
#ページのソースを取得したいとき
driver.page_source
#ウインドウを閉じたいとき
driver.close()
#すべてのウインドウを閉じたいとき
driver.quit()
```

```python
#ある要素をクリックしたいとき
driver.find_element_by_xpath("XPATH").click()
#ある要素までスクロールしたいとき
from selenium.webdriver.common.action_chains import ActionChains

element = driver.find_element_by_id("ID")
actions = ActionChains(driver)
actions.move_to_element(element)
actions.perform()
#テキストを入力したいとき
driver.find_element_by_id("ID").send_keys("strings")
#ウインドウサイズを最大にしたいとき
driver.maximize_window()
#要素が表示されているかどうかを判定したいとき
driver.find_element_by_xpath("xpath").is_displayed()

#参考https://qiita.com/mochio/items/dc9935ee607895420186
```

