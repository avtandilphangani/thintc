#cron-ის გააქტიურება

  TinyCore-ში საჭიროა შემდეგი ნაბიჯები:

/opt/bootlocal.sh ფაილში უნდა დავამატოთ შემდეგი:

> crond -L /dev/null 2>&1

ეს cron-ს გააქტიურებს ყოველი ჩატვირთვისას

შემდეგი ბრძანება:

> crontab -e 

tc მომხმარებლიდან შეიძლება დავარედაგტიროთ  crontab ფაილი:

``` SHELL=/bin/sh
PATH=/usr/sbin:/usr/bin

# run a script each minute
# use absolute paths to point to scripts
* * * * * sh /home/tc/bin 

```

.filetool.sh ფაილში უნდა დაემატოს crontabs, რათა შევძლოთ მათი შენახვა და შემდგომ ჩატვირთვაზე გამოყენება:

echo var/spool/cron >> /opt/.filetool.lst

უნდა გაეშვას backup სკრიპტი, რათა მოხდეს ყველაფერი ცვლილების შენახვა:

> filetool.sh -d
> filetool.sh -b

გადაიტვირთოს TinyCore

გადატვირთვის მერე შემოწმდეს შენახული crontabs რეზერვიდან:

crontab -l