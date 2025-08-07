
layout: posttitle: "Remote Code Execution via Polyglot Web Shell Upload"date: 2025-08-07 23:20:00 +0300categories: security
Remote Code Execution via Polyglot Web Shell Upload

try upload normal image --> (200 OK)![fd35a80e19807dd8a35476e04d85688c.png]({{ site.baseurl }}/images/fd35a80e19807dd8a35476e04d85688c.png)
try upload php file --> (403 Forbidden)![616ddded111512757c259b8224bc59de.png]({{ site.baseurl }}/images/616ddded111512757c259b8224bc59de.png)
Use Polyglot.![8fbd5549c90208785190d723e1dc57bd.png]({{ site.baseurl }}/images/8fbd5549c90208785190d723e1dc57bd.png)

python polyglot_generator.py --input Astro.jpg --shell New.php --type jpeg --output polyglot.php


Upload Polyglot file, and it accept it like image![74ece63ff5d61990b2a4add1322b6d41.png]({{ site.baseurl }}/images/74ece63ff5d61990b2a4add1322b6d41.png)![bea5f4a73e7126ebb9e98b942ded9c8c.png]({{ site.baseurl }}/images/bea5f4a73e7126ebb9e98b942ded9c8c.png)
Open Polyglot file, scrolling to down.![1ac9a30e279ed120560cb0b21a330a7a.png]({{ site.baseurl }}/images/1ac9a30e279ed120560cb0b21a330a7a.png)
Solved![71f34a44f51fc260dc4aebab7bec48a5.png]({{ site.baseurl }}/images/71f34a44f51fc260dc4aebab7bec48a5.png)
