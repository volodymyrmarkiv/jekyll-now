---
layout: post
title: Повідомдення \"cannot change locale\" у CentOS та Amazon Linux
date: 2021-05-16
categories: Linux Locales Amazon CentOS
---

Інколи на свіжовстановленому CentOS 7 чи Amazon Linux 2 можна зустріти повідомлення типу: "warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory"

![locale]({{ site.baseurl }}/images/20210516/locale.png)

Щоб його позбутись достатньо у терміналі **на сервері** від користувача **root** виконати: 

`echo -e "LANG=en_US.utf-8\nLC_ALL=en_US.utf-8" >> /etc/environment`

Або через sudo:

![locale-1]({{ site.baseurl }}/images/20210516/locale-1.png)

`sudo tee -a /etc/environment > /dev/null <<EOF`  
`LANG=en_US.utf-8`  
`LC_ALL=en_US.utf-8`  
`EOF`  

Після перезавантаження чи реконекту по SSH повідомлення пропаде.