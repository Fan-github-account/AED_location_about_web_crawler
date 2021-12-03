# AED_location_about_web_crawler_programing_recording
AED location for Kaohsiung, and just recording for fun.

This program data is based on the AED data of Kaohsiung. I would upload the raw data and my data for location comparing.
[AED data web](https://data.gov.tw/dataset/128664?fbclid=IwAR3rw0tzp3Qmc3zx4DB9GLRNPRUkZBBdK3Fzm4oEgm40aUojUVPnCPLu2m0)

I found that some place about the LNG and LAT in data was wrong.
Its location didn't correspond to the location on the google map.
Thus, if you try to find the location by LNG and LAT on google, it would be wrong place or the LAT and LNG on above is wrong.
![image](https://user-images.githubusercontent.com/77832676/144640013-b72a16cf-99a3-4f1c-93d3-79139392662c.png)
![image](https://user-images.githubusercontent.com/77832676/144640043-510e6004-47bf-4689-817b-e1eee52703c0.png)

Like the picture show above.

Thus, I relocated the place and find those AED place LAT and LNG on google map or other websites.

## The first step 

Of course, the first thing you expect is using the web crawler to get the data on google map.
There are different types of google map search URL.
1. https://www.google.com/maps/search/  +'place'
2. https://www.google.com/maps/place/   +'place' 
3. https://www.google.com/maps/place?=  +'place'

and, by the data of AED place, you could find the 'place name' and the 'place address' in the file.
Doing the permutation search and comparing the results, program choose the most likely one.

![image](https://user-images.githubusercontent.com/77832676/144641668-150ca299-fdbf-424d-88d2-945fedb9c74f.png)
The above is the partial code I writed and I use is to find the LAT and LNG of google version.
and this one would have a little problem is the LNG data might be like 120 -> 20, losing one digit.
Thus,finding those case, we should modify it. 

## The second step 
I found that the google would block the machine querying their data too much.
I have to found another way to query the LAT and LNG data and I found this website.
[webpage](https://medium.com/%E8%8A%B1%E5%93%A5%E7%9A%84%E5%A5%87%E5%B9%BB%E6%97%85%E7%A8%8B/geocoding-%E6%89%B9%E9%87%8F%E8%99%95%E7%90%86%E5%9C%B0%E5%9D%80%E8%BD%89%E6%8F%9B%E7%B6%93%E7%B7%AF%E5%BA%A6-721ab2564c88)

It show how to use the webdriver to do web crawling in another website.
I use this one and I set the environment well in the colab. reference: [stackoverflow](https://stackoverflow.com/questions/51046454/how-can-we-use-selenium-webdriver-in-colab-research-google-com)

However the problem is coming.
![image](https://user-images.githubusercontent.com/77832676/144643425-4778a0fb-cf2e-4964-a7b3-dca0fd74a603.png)
It would usually show this error when running the code.
I check the all code is correct and the Xpath query is right. It should be able to find the data well.
Teaching website:
[web1](https://medium.com/marketingdatascience/%E5%8B%95%E6%85%8B%E7%B6%B2%E9%A0%81%E7%88%AC%E8%9F%B2%E7%AC%AC%E4%BA%8C%E9%81%93%E9%8E%96-selenium%E6%95%99%E5%AD%B8-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8find-element-s-%E5%8F%96%E5%BE%97%E7%B6%B2%E9%A0%81%E5%85%83%E7%B4%A0-%E9%99%84python-%E7%A8%8B%E5%BC%8F%E7%A2%BC-b66920fc8cab)
[web2](https://www.itread01.com/content/1544614812.html)

when I was confusing about this error, I found a webpage talking about this thing.
[why web](https://www.ruyut.com/2020/03/java-selenium-iframe.html)

This talk about why selenium cannot get the data using the Xpath and how to do but I found the teaching material have dealt with this situation. 
and using the dr.switchTo().frame("frameId");  
but the outcoming is bad.


## The third step 

Thus, I begin want to know how to conqur those problem.
At final, I choose breaking the raw data into many parts and use the virtual mechine to process those data.
When the data are all processed, I combine them together.

and the other solution are like the time delay(useless) or changing IP through the VPN.   




