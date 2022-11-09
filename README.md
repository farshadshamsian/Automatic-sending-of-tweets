# Automatic-sending-of-tweets
With the python code that I put, you can easily send your tweets to several different accounts without needing time and copying and pasting repeatedly.



#How to use the code (my suggestion)


1- First of all, install the pycharm software, which is a very famous Python IDE, and then install the Selenium Web Driver package.



2- And then download the latest version of Chrome Driver similar to your Chrome version from the link below and put it in a folder preferably in Driver C

https://chromedriver.chromium.org/downloads



3- And enter the required values according to the explanations I put in the code



	import time

	from selenium import webdriver
	from selenium.webdriver.chrome.service import Service
	from selenium.webdriver.common.by import By
	from selenium.webdriver.support.ui import WebDriverWait
	from selenium.webdriver.support import expected_conditions as EC


	chrome_web_driver = Service("C:\Chrome Driver\chromedriver.exe")  #Enter the absolute path to the directory where the Chrome driver is located
	driver = webdriver.Chrome(service=chrome_web_driver)
	wait = WebDriverWait(driver, 300)
	driver.get("https://twitter.com/i/flow/login")
	driver.set_window_position(0, 0)
	driver.set_window_size(1280, 900)   #Set the screen size of the Chrome browser
	number = 1

	-> email
	email = wait.until(EC.element_to_be_clickable((By.XPATH, '//*[@id="layers"]/div/div/div/div/div/div/div[2]/div[2]/div/div/div[2]/div[2]/div/div/div/div[5]/label/div/div[2]/div/input')))
	email.clear()
	email.send_keys("")   #Enter the email between double quotes




	-> next_button
	next_button = wait.until(EC.element_to_be_clickable((By.XPATH, '//*[@id="layers"]/div/div/div/div/div/div/div[2]/div[2]/div/div/div[2]/div[2]/div/div/div/div[6]/div')))
	next_button.click()


	-> password
	password = wait.until(EC.element_to_be_clickable((By.XPATH, '//*[@id="layers"]/div/div/div/div/div/div/div[2]/div[2]/div/div/div[2]/div[2]/div[1]/div/div/div[3]/div/label/div/div[2]/div[1]/input')))
	password.clear()
	password.send_keys("")  -> Enter the password between double quotes


	-> login
	login_button = wait.until(EC.element_to_be_clickable((By.XPATH, '//*[@id="layers"]/div/div/div/div/div/div/div[2]/div[2]/div/div/div[2]/div[2]/div[2]/div/div[1]/div/div/div/div')))
	login_button.click()


	while number < 51:
		-> new_tweet
		new_tweet = wait.until(EC.element_to_be_clickable((By.XPATH, '//*[@id="react-root"]/div/div/div[2]/header/div/div/div/div[1]/div[3]/a/div')))
		time.sleep(8)
		driver.execute_script("arguments[0].click();", new_tweet)
		
		-> You can send as many tweets as you want, you can create a TXT file and put the text of your tweets in them, also start from 1 and then 2...
		with open(f"{number}.txt", mode="r", encoding="utf-8") as file: -> Enter the absolute path to the directory
			tweet_text = file.read()


		-> tweet_text_input
		tweet_text_input = wait.until(EC.element_to_be_clickable((By.XPATH, '//*                                          [@id="layers"]/div[2]/div/div/div/div/div/div[2]/div[2]/div/div/div/div[3]/div/div[1]/div/div/div/div/div[2]/div[1]/div/div/div/div/div/div[2]/div/div/div/div/label/div[1]/div/div/div/div/div/div[2]/div')))
		tweet_text_input.clear()
		tweet_text_input.send_keys(f"{tweet_text}")
		tweet_text_input.send_keys("\n")
		tweet_text_input.send_keys("")  -> Enter the hashtag you want

		time.sleep(10)
		print(number)
		number += 1



		-> submit_tweet
		submit_tweet = wait.until(EC.element_to_be_clickable((By.XPATH, '//*[@id="layers"]/div[2]/div/div/div/div/div/div[2]/div[2]/div/div/div/div[3]/div/div[1]/div/div/div/div/div[2]/div[3]/div/div/div[2]/div[4]')))
		time.sleep(8)
		driver.execute_script("arguments[0].click();", submit_tweet)








