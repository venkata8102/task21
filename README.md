from selenium import webdrive
driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/")
print("Cookies before login:", driver.get_cookies())
driver.find_element_by_css_selector("input#user-name").send_keys("standard_user")
driver.find_element_by_css_selector("input#password").send_keys("secret_sauce")
driver.find_element_by_css_selector("input.btn_action").click()
assert "https://www.saucedemo.com/inventory.html" in driver.current_url
print("User is logged in successfully.")
print("Cookies after login:", driver.get_cookies())
driver.find_element_by_css_selector("button#logout_sidebar_link").click()
assert "https://www.saucedemo.com/" in driver.current_url
print("User is logged out successfully.")
driver.close
