---
layout: post
title: ""Checking inventory at your local Barnes and Noble""
date: 2015-07-03 14:49:10 -0400
comments: true
categories: Python
---
Does anyone really shop or buy at local brick & mortar stores anymore? No? Well, this was still a fun app to make.

A few days ago someone in a forum I frequent posted that they keep a list of bookmarks to bn.com that told them stock levels for their local BN but something had changed and the link was no longer working.

What he had to do now was go to the specific item page, click a button that would open up a search by zip box, enter the zip, then get a modal telling him if it was in stock. He wanted to know if there was a way to link directly to the pop-up.

I did a search for The Martian by Andy Weir, poked around the item page and the modal using Chrome dev tools and didn't see a way to link directly to the modal but I did find something interesting!

While they only told you if the item was In Stock or not the return response provided you with quite a bit of other information! Including the number the store has on hand.

{% img /images/dev_tools.png 'image' 'images' %}

BN is requiring custom headers to get to the response via http but if you right click on the Name of the file in the Network tab of Dev tools you can choose `Copy as cURL`. Paste that into a terminal window and you get the json response back for that item!.

```bash
curl 'http://stores.barnesandnoble.com/ris/inventory?ean=0670541597682&page=1&pageSize=5&zipcode=22911' -H 'ris-zip: 22911' -H 'Accept-Encoding: gzip, deflate, sdch' -H 'Accept-Language: en-US,en;q=0.8' -H 'ris-chash: e0a986c0f4f2defbe1218df7f050dcb1' -H 'ris-appsig: bc9a6da9d84f82a1048b52e058a0eff7' -H 'Cookie: TS01e75984_76=08ea36dc92ab2800efd856ac2f7d30201365d091bb47de8b2d3be5964994f0f6c5a50db942b6f40f434d0d2c7c77c48608f8b9c31a87f800ef62a9c7eac1075345cef3282d782d18aa54589386a7c3608f3fc60cecf03f5ffe4bc3487d55554999902bcb466ef9f5f485e875c1e8d44835339daf27f4ab6c7690714708a7c4874897b81ce3feaeb51db92d10aac5c26bc285fee97bcc39f78f695c07e88e24d1e51edb2e7c55aecf101d23559ac2985478ad9cf6c98df8c558d2991018acdf217493b70dd8f7f8879242cbc60b256687e1bb2b6a3e0400023026e1f14e3971213eff1d8f6bbbac0c0020bcae0d515a02096c1850538bf79510ac65bea231ee0545079a706bdbb051e519afb8701270265d72a2543cb49ba2060e39eb18b3789765d95eed4f288a4169202b31ff1a8fd6; JSESSIONID=Jqkh0Ej4GrQyRU0l22mi7Gmv; TS01cdc16d=01b22697604b1912c5bdc420b66e39c850afb865bd6dc3ef4749d23d80be419f7ed6d20da0450efdf480fa9cb6b55d2ed776258918; DeviceType=Desktop; showSiteAs=Desktop; client-profile=Desktop; TS01af0a8e=01b2269760af1d36cb4fb5b7ca692976712a5a4967599fe0d92b4d461161ec5546daabbaf985f7aee29c78c510273b9641b2400b03ba398c602fa8f53a55c470ada9317dc274f5309eb70a67d500b94d8bc3967ea9; AMCV_9A223704532965F10A490D44%40AdobeOrg=1256414278%7CMCMID%7C87343886875634417124019563558639690053%7CMCAAMLH-1436405345%7C7%7CMCAAMB-1436405345%7CNRX38WO0n5BH8Th-nqAG_A%7CMCAID%7CNONE; BIGipServerwby-fe-cseap-pool_8080=!r4eYi3prBznUjIadz57UnRO+XgUP9GBXYJfEiZiVWLXTTCnzTWp5rZ04wSAzFGUwaHq6wRb8mxEIvSY=; BIGipServerwby-fe-caiws-pool_80=!Z9RlgWru6D6gob6dz57UnRO+XgUP9L0vERSL4mYexaoUiHw4Fi8ZummU6q36Ngq8oou4t0cx+H0TbBU=; __gads=ID=afd12464bf4e9ede:T=1435934093:S=ALNI_MY-qv9PAulhhBNeDsi8gI_pQrJPUg; __qca=P0-1566046451-1435934094100; s_vnum=1438401600945%26vn%3D7; ADRUM=s=1435948949240&r=http%3A%2F%2Fwww.barnesandnoble.com%2Fs%2Fdead%2Bof%2Bwinter%3F-119814330; _ga=GA1.2.396886361.1435800545; s_cc=true; RT=; s_invisit=true; s_depth=10; s_lv=1435949667207; s_lv_s=Less%20than%201%20day; TS01e75984_27=014a7c9820ca1a3947ea741b05132d8a885f8cea36ffe609379a58536d96879aaae5d69311f62543b4d861c7f03c05bd3c4541cf9d; TS01e75984=01b22697609a9717ceff3263c877f56b460b919f8036a719ac8691a5803d05c8f6122d12c52b2c5bebf0cdc90c0ef5a3452c8b5e7889135d6accf7433d07dc5d794d82006e' -H 'ris-email: ' -H 'Connection: keep-alive' -H 'ris-appts: 1435949667246' -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/43.0.2357.130 Safari/537.36' -H 'ris-price: 53.95' -H 'Accept: application/json, text/plain, */*' -H 'Referer: http://stores.barnesandnoble.com/ris/reservation.jsp?zipcode=22911&price=53.95&email=&chash=e0a986c0f4f2defbe1218df7f050dcb1&appid=bndotcom&appsig=bc9a6da9d84f82a1048b52e058a0eff7&ean=0670541597682&appts=1435949667246&' -H 'ris-ean: 0670541597682' -H 'ris-appid: bndotcom' --compressed
```

That's great and all but how are we going to put this into a script to make it usable?

Heading to this page you can convert cURL to Python requests. [http://curl.trillworks.com/](Convert cURL to Python). Paste the cURL command in, click the button, and copy your Python code!

You'll get something that looks like this:

```python
cookies = {
    'TS01e75984_76': '08ea36dc92ab2800efd856ac2f7d30201365d091bb47de8b2d3be5964994f0f6c5a50db942b6f40f434d0d2c7c77c48608f8b9c31a87f800ef62a9c7eac1075345cef3282d782d18aa54589386a7c3608f3fc60cecf03f5ffe4bc3487d55554999902bcb466ef9f5f485e875c1e8d44835339daf27f4ab6c7690714708a7c4874897b81ce3feaeb51db92d10aac5c26bc285fee97bcc39f78f695c07e88e24d1e51edb2e7c55aecf101d23559ac2985478ad9cf6c98df8c558d2991018acdf217493b70dd8f7f8879242cbc60b256687e1bb2b6a3e0400023026e1f14e3971213eff1d8f6bbbac0c0020bcae0d515a02096c1850538bf79510ac65bea231ee0545079a706bdbb051e519afb8701270265d72a2543cb49ba2060e39eb18b3789765d95eed4f288a4169202b31ff1a8fd6',
    'JSESSIONID': 'Jqkh0Ej4GrQyRU0l22mi7Gmv',
    'TS01cdc16d': '01b22697604b1912c5bdc420b66e39c850afb865bd6dc3ef4749d23d80be419f7ed6d20da0450efdf480fa9cb6b55d2ed776258918',
    'DeviceType': 'Desktop',
    'showSiteAs': 'Desktop',
    'client-profile': 'Desktop',
    'TS01af0a8e': '01b2269760af1d36cb4fb5b7ca692976712a5a4967599fe0d92b4d461161ec5546daabbaf985f7aee29c78c510273b9641b2400b03ba398c602fa8f53a55c470ada9317dc274f5309eb70a67d500b94d8bc3967ea9',
    'AMCV_9A223704532965F10A490D44%40AdobeOrg': '1256414278%7CMCMID%7C87343886875634417124019563558639690053%7CMCAAMLH-1436405345%7C7%7CMCAAMB-1436405345%7CNRX38WO0n5BH8Th-nqAG_A%7CMCAID%7CNONE',
    'BIGipServerwby-fe-cseap-pool_8080': '!r4eYi3prBznUjIadz57UnRO+XgUP9GBXYJfEiZiVWLXTTCnzTWp5rZ04wSAzFGUwaHq6wRb8mxEIvSY=',
    'BIGipServerwby-fe-caiws-pool_80': '!Z9RlgWru6D6gob6dz57UnRO+XgUP9L0vERSL4mYexaoUiHw4Fi8ZummU6q36Ngq8oou4t0cx+H0TbBU=',
    '__gads': 'ID=afd12464bf4e9ede:T=1435934093:S=ALNI_MY-qv9PAulhhBNeDsi8gI_pQrJPUg',
    '__qca': 'P0-1566046451-1435934094100',
    's_vnum': '1438401600945%26vn%3D7',
    'ADRUM': 's=1435948949240&r=http%3A%2F%2Fwww.barnesandnoble.com%2Fs%2Fdead%2Bof%2Bwinter%3F-119814330',
    '_ga': 'GA1.2.396886361.1435800545',
    's_cc': 'true',
    'RT': '',
    's_invisit': 'true',
    's_depth': '10',
    's_lv': '1435949667207',
    's_lv_s': 'Less%20than%201%20day',
    'TS01e75984_27': '014a7c9820ca1a3947ea741b05132d8a885f8cea36ffe609379a58536d96879aaae5d69311f62543b4d861c7f03c05bd3c4541cf9d',
    'TS01e75984': '01b22697609a9717ceff3263c877f56b460b919f8036a719ac8691a5803d05c8f6122d12c52b2c5bebf0cdc90c0ef5a3452c8b5e7889135d6accf7433d07dc5d794d82006e',
}

headers = {
    'ris-zip': '22911',
    'Accept-Encoding': 'gzip, deflate, sdch',
    'Accept-Language': 'en-US,en;q=0.8',
    'ris-chash': 'e0a986c0f4f2defbe1218df7f050dcb1',
    'ris-appsig': 'bc9a6da9d84f82a1048b52e058a0eff7',
    'ris-email': '',
    'Connection': 'keep-alive',
    'ris-appts': '1435949667246',
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/43.0.2357.130 Safari/537.36',
    'ris-price': '53.95',
    'Accept': 'application/json, text/plain, */*',
    'Referer': 'http://stores.barnesandnoble.com/ris/reservation.jsp?zipcode=22911&price=53.95&email=&chash=e0a986c0f4f2defbe1218df7f050dcb1&appid=bndotcom&appsig=bc9a6da9d84f82a1048b52e058a0eff7&ean=0670541597682&appts=1435949667246&',
    'ris-ean': '0670541597682',
    'ris-appid': 'bndotcom',
}

requests.get('http://stores.barnesandnoble.com/ris/inventory?ean=0670541597682&page=1&pageSize=5&zipcode=22911', headers=headers, cookies=cookies)
```
Let's import `requests` (be sure to install requests if you don't already have it!) and add the Python code we just got. It turns out we don't need the cookies dictionary so we're going to remove that and at the end let's put the return into a variable.

```python
import requests

headers = {
    'ris-zip': '22911',
    'Accept-Encoding': 'gzip, deflate, sdch',
    'Accept-Language': 'en-US,en;q=0.8',
    'ris-chash': 'e0a986c0f4f2defbe1218df7f050dcb1',
    'ris-appsig': 'bc9a6da9d84f82a1048b52e058a0eff7',
    'ris-email': '',
    'Connection': 'keep-alive',
    'ris-appts': '1435949667246',
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/43.0.2357.130 Safari/537.36',
    'ris-price': '53.95',
    'Accept': 'application/json, text/plain, */*',
    'Referer': 'http://stores.barnesandnoble.com/ris/reservation.jsp?zipcode=22911&price=53.95&email=&chash=e0a986c0f4f2defbe1218df7f050dcb1&appid=bndotcom&appsig=bc9a6da9d84f82a1048b52e058a0eff7&ean=0670541597682&appts=1435949667246&',
    'ris-ean': '0670541597682',
    'ris-appid': 'bndotcom',
}

r = requests.get('http://stores.barnesandnoble.com/ris/inventory?ean=0670541597682&page=1&pageSize=5&zipcode=22911', headers=headers)
}
```

Run this at the terminal and you should get the same return response we saw in dev tools.

Want to see that in a better format? At the top add `from pprint import pprint`.

Then we're going to call the .json() method on the return to get a Python dictionary we can work with.

```
r = r.json()
pprint(r)
```

```
{'content': {'distance': 10,
             'ean': '9780553418026',
             'firstPage': True,
             'inventoryLoadDate': '2015-07-03 04:00:00',
             'inventoryReservable': 1,
             'lastPage': True,
             'page': 1,
             'pageCount': 1,
             'pageSize': 5,
             'product': {'availableOn': 1414468800000,
                         'categoryDesc': 'Science Fiction',
                         'createdAt': 1419263528000,
                         'displayEan': '9780553418026',
                         'ean': '9780553418026',
                         'formatDescription': 'Trade Paper',
                         'pageCount': 400,
                         'price': '15',
                         'publisherName': 'Crown Publishing Group',
                         'subjectDesc': 'Sf/Fantasy',
                         'title': 'Martian',
                         'updatedAt': 1419263528000},
             'searchZipcode': '22911',
             'stores': [{'address1': 'Barracks Road Shopping Center',
                         'address2': '1035 Emmet St Suite A',
                         'city': 'Charlottesville',
                         'distance': 3.8863318,
                         'divisionId': 1,
                         'hours': 'Sun 9-9, Mon-Thurs 9-10, Fri & Sat 9-11',
                         'hoursHtml': 'Sun 9-9,<br> Mon-Thurs 9-10,<br> '
                                      'Fri & Sat 9-11',
                         'inventory': 41,
                         'inventoryDate': '2014-10-28 04:00:00',
                         'inventoryLoadDate': 1435896000000,
                         'name': 'Charlottesville',
                         'pageSize': 5,
                         'phone': '434-984-0461',
                         'reservable': True,
                         'resultId': 1,
                         'retailPrice': 15.0,
                         'state': 'VA',
                         'storeId': 2559,
                         'storeReservable': 1,
                         'zipcode': '22903'}],
             'totalCount': 1},
 'statusCode': 200,
 'statusText': 'OK'}
```

Inside the `stores` array is an `inventory` key that shows us the number of items that store has in stock!

Let's grab it...

`print(r['content']['stores'][0]['inventory'])`

But we want it to read a little better so let's add in some Python string interpolation:

`print("There are {} in stock.".format(r['content']['stores'][0]['inventory']))`

Gist of all the code: https://gist.github.com/jhwhite/3cfd02186e577db7a7e0

##Summary
I've actually done a little bit more with this here, http://nyt-bestsellers-at-bn.herokuapp.com/.

In the next blog post I'll go into using the NYT Books API and checking Barnes and Noble stock against that, then in another blog post I'll write about how to put it all together using a Python microframework called Flask.