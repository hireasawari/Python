from bs4 import BeautifulSoup
import requests
import smtplib

url="https://appbrewery.github.io/instant_pot/"
response=requests.get(url)


soup=BeautifulSoup(response.content,"html.parser")
#print(soup.prettify())
price_tag=soup.find(name="span",class_="a-offscreen")
price=float(price_tag.string.split("$")[1])
print(price)
def to_email():
    if (price==99.99):
        print("email sent")
        my_email = "hireriya2005@gmail.com"
        password = "**********"

        connection = smtplib.SMTP("smtp.gmail.com")
        connection.starttls()

        connection.login(user=my_email, password=password)
        connection.sendmail(from_addr=my_email, to_addrs="hireasawari@gmail.com",
                            msg=f"Subject: Price drop \nGo and buy the hot pot soon!! \n\n {url}")

        connection.close()

to_email()
