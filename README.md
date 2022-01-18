# Script-Scrapping
setwd("D:\\Anis\\KULIAH\\DATA SEMESTERAN\\SKRIPSI\\twitter")

install.packages("twitteR")
install.packages("ROAuth")
install.packages("RCurl")

library(twitteR)
library(ROAuth)
library(RCurl)


download.file(url="http://curl.haxx.se/ca/cacert.pem",destfile="cacert.pem")

reqURL <- "https://api.twitter.com/oauth/request_token"
accessURL <- "https://api.twitter.com/oauth/access_token"
authURL <- "https://api.twitter.com/oauth/authorize"
CUSTOMER_KEY <- "" #consumerAPIkey
CUSTOMER_SECRET <- "" #APISecretkey
ACCESS_TOKEN <- ""#Accesstoken
ACCESS_secret<- ""#Accesstokensecret

setup_twitter_oauth(CUSTOMER_KEY, CUSTOMER_SECRET, ACCESS_TOKEN, ACCESS_secret)

#Mengambil data dari twitter

tw<-searchTwitter('pembelajaran tatap muka', n=2000 , since="2021-03-19",until="2021-10-30")
tw.df<-twListToDF(tw) 
head(tw.df$created)
tail(tw.df$created)
#Menyimpan Data Hasil Crawling
data.tw=data.frame(tw.df)
text=data.tw[1]
lain=data.tw[2:16]
write.csv(text,file = 'D:\\Anis\\KULIAH\\DATA SEMESTERAN\\SKRIPSI\\twitter\\tatapmuka4.csv')
