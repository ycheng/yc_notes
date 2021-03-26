On Focal, step 1:
```
sudo apt-get install python3-selenium --no-install-recommends
sudo apt-get install firefoxdriver firefox-geckodriver
```

The code is like
```
#! /usr/bin/python3
import datetime

from selenium import webdriver
from selenium.webdriver.common.keys import Keys

    try:
        driver = webdriver.Firefox()
        driver.get("http://blala/")

        print("sleep 1")
        time.sleep(1)

        print("sleep 1 done")
        # aas = driver.find_elements_by_tag_name("button")
        buttonStarts = driver.find_elements_by_id("buttonStart data collection")
        for btn in buttonStarts:
            if (btn.is_displayed()):
                btn.click()
                break
            else:
                continue
```
