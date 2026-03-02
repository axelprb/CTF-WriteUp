Write-up Internal Selection HCS CTF 2025
========================================


**guessr 1**
------------

![captionless image](https://miro.medium.com/v2/resize:fit:1000/format:webp/1*UnkTrkyjS-q_DuY5r2mXNg.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*BdLVgkAW_Wloxz4HeTIGvg.png)

ngeliat helm di gambarnya sih saya langsung nebak ini harusnya sebuah circuit. Dan langsung saya coba buat google lens helmnya dan dapet sebuah circuit bernama Circuit de Spa di Belgia

![captionless image](https://miro.medium.com/v2/resize:fit:878/format:webp/1*UppgYaHF7twcMOuvgdmtZg.png)

Dan setelah coba menjelajah di sekitar Circuit de Spa, saya mendapat lokasi dekat sebuah gate circuit dan mendapat flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*GOts6Hdi5UooxPhQDWMenQ.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**guessr 2**
------------

![captionless image](https://miro.medium.com/v2/resize:fit:1008/format:webp/1*FAAk1Xbnm5bwapzJoINesg.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*LWpFE_CY-ZtyjP07NR6T2A.png)

Langsung saja kita google lens patung yang ada di depan bangunan itu

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*YtAhbnzT0u1InY52eX-LXg.png)

dan ternyata tempatnya ada di sebuah teater di russia yaitu teater vakhtangov di daerah moskow

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Z7N5kbgHjCr3sGcYUKI19A.png)

langsung saja kita pilih tempat pastinya dan dapet flagnya

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**guessr 3**
------------

![captionless image](https://miro.medium.com/v2/resize:fit:998/format:webp/1*u8bPBkUMjbTXP_zJPvvByQ.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*6EaLZZcXJqU5Ohcfge3NkQ.png)

Awalnya saya salfok sama patok biru putih yang bertuliskan DT 317G dan langsung coba saya search di google dan ketemu di sekitar vietnam, thanh thuy. setelah mencari-cari jalanan yang panjang di sekitaran situ akhirnya ketemu juga

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*i2y_eKuX2sCNT2V6Y2YkAQ.png)

tapi nyari di OSINT Platformnya sih harus kerja keras banget

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*xA-YGYXngZ57v0UudywP2w.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**Atadatem**
------------

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*-1F4z092nTgJ5KYLF57frA.png)

Namanya aja Metadata yang dibalik, pasti cara solve nya dengan ngeliat metadata dari file hcs.png. Langsung saja menggunakan exiftool

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*YG1cOxhB73K7cmqtfQa5wg.png)

Disana yang kelihatannya mencurigakan sih yang Comment, Description, dan Title karena kaya encode dari base64. Setelah coba saya gabung-gabung gaaada yang bener. lalu saya salah fokus sama Title yang dimana kayaknya petunjuk urutan decode nya. Langsung aja saya decode

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*b11UkYskBFYyQWk3vMqsrA.png)

sepertinya merujuk ke suatu link pastebin yang isinya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*l8d-n4iJajRVfB92OHmqrg.png)

langsung saya decode dan dapet flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*GnG68VnVG9Eu5eMzVNuRAA.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**I Forgot Something**
----------------------

![captionless image](https://miro.medium.com/v2/resize:fit:1130/format:webp/1*j5hnurRBy6uTa33lKd3NZQ.png)

Saya coba langsung extract file zip nya dan ternyata di password

![captionless image](https://miro.medium.com/v2/resize:fit:882/format:webp/1*84jOVsPUEHttEuYScbEeQA.png)

Dan langsung saja saya brute-force passwordnya dengan wordlist rockyou.txt dan tool fcrackzip

![captionless image](https://miro.medium.com/v2/resize:fit:1212/format:webp/1*QU01fYzL_tcVS4iVKkTDnQ.png)

dan dapet passwordnya “estrella”, langsung saja saya unzip file nya dengan passwordnya.

ternyata ada file flag.txt dan langsung saja kita cat

![captionless image](https://miro.medium.com/v2/resize:fit:1150/format:webp/1*B7ZqEn1_mk4z95VKRog-7g.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**LeFI Gimang**
---------------

![captionless image](https://miro.medium.com/v2/resize:fit:1008/format:webp/1*dn2XoNRyuCG_kLmolc0uyw.png)

karena namanya sendiri LeFI Gimang jadi pastinya ini vulnerability nya LFI atau path traversal. saya coba beberapa payload untuk path traversal.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*8SpRLRlNBztwvU-fx5Do7Q.png)

kita coba ubah request GET nya dan dapet flagnya dengan payload

`_/?query=../../../../flag.txt_`

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**Jinja Ninja**
---------------

![captionless image](https://miro.medium.com/v2/resize:fit:992/format:webp/1*bPtzdxTN7McmrUALYuEQoA.png)

Dari namanya seharusnya ini SSTI with jinja2. Kita coba dulu untuk masukkin payload sederhana SSTI seperti `{{3*3}}` dan ternyata menghasilkan angka 9 yang artinya payload saya tereksekusi oleh server.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*imO179oEmlAEXwuN0mnOrw.png)

Jadi langsung saja kita gunakan payload RCE SSTI jinja2 , yaitu

`_{{request[‘application’][‘__globals__’][‘__builtins__’][‘__import__’](‘os’)[‘popen’](cat /flag)[‘read’]()}}_`

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*yBFccVVNXXHHnAN0RENrmg.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**Lockpicking**
---------------

![captionless image](https://miro.medium.com/v2/resize:fit:1024/format:webp/1*5CRFA4nVF36Tkj7mI9HikA.png)

Ngeliat web kaya begini sih

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*gRaqWs0KNk9bVxOr2Y_SJQ.png)

saya langsung pengennya nyoba payload sql injection, ditambah lagi disitu tertulis “This login accepts many public payloads”. Jadinya saya nyoba payload SQL Injection `' OR '1` dan masuk

![captionless image](https://miro.medium.com/v2/resize:fit:1094/format:webp/1*YNtN0swlensv_82zJZjubw.png)

Tapi untuk kali ini webnya membatasi beberapa karakter untuk di input sehingga saya coba gunakan `'='` dan dapet flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*qanXCpf8PcdgYlLC29F3NQ.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

check it out
------------

![captionless image](https://miro.medium.com/v2/resize:fit:1008/format:webp/1*Bc4OGWX5rfFirl2IYble2w.png)

ya sesuai namanya tinggal di cek aja kodenya trus tinggal di arrange ulang aja flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Nyok_njK5KbFtv8vh_ZYtg.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

strings
-------

![captionless image](https://miro.medium.com/v2/resize:fit:1048/format:webp/1*5WXTScJiUuc8z3JAwXm2rg.png)

sesuai namanya strings, langsung aja pakai tool strings untuk ngambil semua strings yang ada di file chal, dan langsung aja kita dapet flagnya.

![captionless image](https://miro.medium.com/v2/resize:fit:1240/format:webp/1*B0jHDIo2xDDqnDahazVUuw.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**WASM (Weird Assembly)**
-------------------------

![captionless image](https://miro.medium.com/v2/resize:fit:1014/format:webp/1*x_UXA6fCsMtNfWNSf9M5YA.png)

Seperti biasa awal-awal saya coba strings dulu filenya.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*s8CSWGsAMNCqR-d2yD8KKw.png)

ternyata isinya file assembly dan ada susunan kata yang dari nama-nama bunga yang sebelumnya jika di scroll itu di assign ke huruf alphabet dan beberapa karakter. Langsung saja kita buat scirpt sederhana untuk mentranslate nama-nama bunga tersebut

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*ZtpGvshPqUlggxNhMBuY-w.png)

dan kita dapet flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1128/format:webp/1*agmK2MLI9X7Rtq5rhUx9sw.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

**sPYware**
-----------

![captionless image](https://miro.medium.com/v2/resize:fit:1036/format:webp/1*3ZF0vh_BCjPOI01yaD9hbw.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*XdGUhWUbirx_VyFQJksSYg.png)

dari kodenya kelihatan kalo banyak karakter yang ga kelihatan karena di spasi banyak banget sama author nya -_-.

![jujur ini biar apa ya…](https://miro.medium.com/v2/resize:fit:768/format:webp/1*Qw91ggR6m_vsc2aWuKzMDA.png)

Langsung saja kita delete-delete karakter yang jauh-jauh

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*TWzRXqd5letoS6TyGv9sBw.png)

dan langsung run aja lalu kita dapat flagnya

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

based
-----

![captionless image](https://miro.medium.com/v2/resize:fit:996/format:webp/1*8dHC5qT6rWy9kyDTMklTNg.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*0Zs6iuuTVHlarwb1wIbnfw.png)

di dalam file zip nya terdapat file txt yang isinya text ter-encode jadi coba kita decode pake cyberchef

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*H5hz1i_7CMM0x67BcpCJuw.png)

Dan ternyata beneran dikubur pake base64 sampe beberapa kali sampe dapet flagnya :)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

Reverse Day 1
-------------

![captionless image](https://miro.medium.com/v2/resize:fit:1016/format:webp/1*aWfGhTLNzX0v6Fhl0-7ovg.png)![captionless image](https://miro.medium.com/v2/resize:fit:1222/format:webp/1*jyUNHLcxqao38J8SyFPUGw.png)

bener kata erlang, gabisa cuman strings doang. mau gamau ya pakenya ghidra ya ges ya.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Y-A8SXhoKsdAQTTQCyzSLQ.png)

setelah di analisis (sok jago), di decompiler saya ketemu suatu function check yang dilihat-lihat kok janggal. sehingga saya coba untuk membuat script reverse nya dengan bantuin teman baik saya yaitu google gemini :)

![captionless image](https://miro.medium.com/v2/resize:fit:1156/format:webp/1*iwhEPoi4Gi0WDJEGJngFbg.png)![captionless image](https://miro.medium.com/v2/resize:fit:754/format:webp/1*CvtuGlA9GBULK7HosVaVbw.png)

dan kita mendapat flagnya :).

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

decodescii
----------

![captionless image](https://miro.medium.com/v2/resize:fit:1010/format:webp/1*qY5GA4trSKoPnbv3pEbCMA.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*VrhxoOgRrM7r-CtewF2xcQ.png)

Waktu saya coba netcat ternyata ada hint sebuah kalimat dari hexa decimal dan kita coba decode

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*6Ya1fOJUDFqv5pxZrzfPQw.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*GlUF9OS3WnPYcOM9EJ8sDg.png)

dan ternyata kalo kita masukkin ke cipher identifier terdeteksi bahwa kalimat di encode dengan leet speak 1337

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*HSIFZI-o9efr_gWaxFX3Mw.png)

dapet lagi kalimat yang mirip nato phonic yang kalo kita decode lagi akan muncul

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*kojWi_rzIK5t53rbRhnMDA.png)

disitu terbaca bahwa key nya 1312 dan langsung saja kita masukkan ke terminal

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Sxru8oH8m3OfWx7nWDB98Q.png)

dan dapet lagi tuh encoded message yang kalo kita deteksi itu merupakan base45

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*vZgd9F0gZY5HCS-QhG_yBg.png)

lalu setelah kita decode, dapet sebuah string dari base32

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*wjYhsYmy3J-JVTWT2uuq_g.png)

dan dapatlah sebuah encoded string lagi (jujur cape decodenya) tapi lebih gampang karna cuma geser huruf aja yang harusnya jadi sebuah link yang ternyata keluarnya begini

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*mppByaW9Iea0e3EUK_aS2g.png)

jadi di terminal saya coba masukkin aja link nya dan bener itu jawabannya. Nah tiba-tiba ada encoded string lagi -_-.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*KXsBsqP51T3wy5jhZBlGkg.png)

yaudah langsung decode lagi dah dan saya dapet link yang mengarah ke asciidots. Nah disini disuruh nebak” input terendah yang bisa di submit. Trik saya setelah lama ngesolvenya adalah cari batas maksimal ratusribuan supaya ga terlalu banyak bruteforce nya sambil ngetik2 asal di terminal supaya ga mati :). beberapa kali sampai jutaan baru berhasil jadi terpaksa ngulang netcatnya sampe dapet batas yang rendah (jujur ini smartmove gasi hehe..) .akhirnya solve juga walaupun gapaham sama hint monotonic function domain

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*d2QtWLyVUDEq8ATAfgSplA.png)

jujur bikin wu nya soal ini susah..

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

L3AK
----

![captionless image](https://miro.medium.com/v2/resize:fit:1022/format:webp/1*lIBDB39vStofqhXYlJJB6Q.png)

Sbenernya kriptografi ini saya tidak terlalu mengerti namun saya berusaha coba mengerti minimal 1–2 soal. Nah untuk soal ini ternyata vulnerabilities nya terdapat pada line 12 yaitu pada `what =d % (p-1)` yang nanti dipakai untuk menemukan faktor prima dari n

![captionless image](https://miro.medium.com/v2/resize:fit:924/format:webp/1*qA33GOCBcKjx3NWFVjOVJQ.png)

Nah setelah menggunakan bantuin teman baik saya lagi-lagi gemini untuk mensolve dan menggunakan variabel di output.txt, saya mendapat pula flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*vdhJbjSZnOVB7QyOUancoA.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

elefay
------

![captionless image](https://miro.medium.com/v2/resize:fit:1022/format:webp/1*H2XU7aO6UhHMgqQSEvp1Rw.png)

Sama seperti LFI sebelumnya saya pasti awalnya mengecek path traversal. Ternyata untuk kasus ini path travelsal tidak bisa dilakukan karena web sudah bisa memfilter payload seperti `flag.txt;../;../../` atau payload polosan lainnya.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*e6bs3rnNFZleaLoZXSrbEg.png)

saya coba teknik obfuscation jadi payload `../` akan saya ubah menjadi `....//` namun masih belum bisa.

Nah, tiba-tiba dapet ide buat setting payload `flag.txt` dengan `flflag.txtag.txt` jadi ketika sistem detect flag.txt otomatis bakal dihapus dan menyisakan `flag.txt` yang di dalem.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*oE0nO75AW0inlqEu8FHcOw.png)

dan dapet dah flagnya.

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

Wordle
------

![captionless image](https://miro.medium.com/v2/resize:fit:1016/format:webp/1*z7VX0AMWEKUZSRO4VYFYwg.png)

apa yang bisa saya WU kalo soal wordle begini :)

berikut ss-an saya dapet flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Xh2FXXE7-CFxWIdRXqo7rg.jpeg)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

Tuff Shop
---------

![captionless image](https://miro.medium.com/v2/resize:fit:1002/format:webp/1*JDPKOjcCrerH_wW4GOgXDg.png)![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*OLrFJjJNQVizRnTIKQZ7Zw.png)

saya nyoba-nyoba cari payload-payload dengan bruteforce, dan pas enter quantity 999999999 malah bikin uang nambah. Yaudah langsung beli flag aja dan dapet deh flag

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

Blind File
----------

![captionless image](https://miro.medium.com/v2/resize:fit:1014/format:webp/1*EeAbnd5JbZa4AfAuLXvaug.png)

kalo binary file gini saya awal-awal pasti strings dulu filenya dan nemu yang janggal kok ada secret…

![captionless image](https://miro.medium.com/v2/resize:fit:626/format:webp/1*rMiuEMbywP6eCCKv7xD3kg.png)

yaudah sayacoba pake binwalk buat extract file yang ada di dalem itu.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*mSGcaC64rR8N-3cWWhommQ.png)

dan bener aja kalo kita liat gambarnya ada flag disitu.

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

Three Umazing Things
--------------------

![captionless image](https://miro.medium.com/v2/resize:fit:1078/format:webp/1*I_6mtO6Pqq7Emd3MfFi9Vw.png)

saya pake 3 tool buat mecahin steganografi di gambar-gambar ini. Toolnya zsteg,binwalk, dan stegseek.

![zsteg sedihakuwak.png](https://miro.medium.com/v2/resize:fit:1092/format:webp/1*pOsnmNqGwzVEarxE-M0m7g.png)![binwalk -e hehe.jpg](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*L6Kyx7LGI5MHZlw_HDfJcQ.png)![stegseek grrrr.jpg /usr/share/wordlists/rockyou.txt](https://miro.medium.com/v2/resize:fit:1074/format:webp/1*MrN-wbcneJj3rmjmXlcWNg.png)

stelah itu langsung di gabung-gabungin aja deh flagnya.

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

My Networ(th)k
--------------

![captionless image](https://miro.medium.com/v2/resize:fit:1006/format:webp/1*q9sAWZD31nx8feYPy2fiPw.png)

Saya cek setiap streamnya dan ketemu encode string yang agak janggal di stream 18

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*PhoBbf54kv7h-pBBN6mGjg.png)

langsung saja kita decode dan bener aja itu flagnya.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*ltYVmY8BAyfrH6uqK_aVuA.png)

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

saya coba mainin gamenya dan langsung inisiatif inspect webnya. Dan saya nemuin assembly nya di sourcenya.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*DTJF7-JvNncCcI81xYfW8w.png)

Nah dengan bantuan teman baik sekaligus saudara saya yaitu google gemini. setelah saya cari tahu ternyata kuncinya adalah menemukan **seed** yang digunakan, yang ternyata dihitung secara static di dalam file JavaScript (`4000600`). abis nemuin seed nya, langsung saja mensimulasikan fungsi `update_on_eat` dari WASM berulang kali hingga variabel `integrity` mencapai nilai target `1904218052`. Setelah kondisi ini terpenuhi, maka kita bisa dapetin flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*pCm1Z_SZEbzjVJpU3ZOq3w.png)

berikut script untuk mendapat flagnya

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*D1QovWMaHH72Rqyy02qS-g.png)

dan dapet juga flagnya

— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —

Hexahue Bergerak
----------------

![captionless image](https://miro.medium.com/v2/resize:fit:1002/format:webp/1*oE-NeMJcaJSB9YuR467TFw.png)

yang pertama saya lakukan pasti nge split framenya satu satu jadi file-file jpg

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*G_fbjZ2CaNOSe5Rp4S5QDg.png)

Nah, lagi-lagi saya mendapat ilmu dari teman saya google gemini sehingga setiap file jpg dapat di baca menjadi teks yang utuh untuk mendapatkan flag

![captionless image](https://miro.medium.com/v2/resize:fit:1082/format:webp/1*SRtI2p4eY3kMO24f2-5fJg.png)

diatas adalah mapping dari warna hexahue

setelah jalanin scriptnya, saya dapet text utuh yang diakhir teks terdapat strings untuk mengisi HCS{flag} yaitu `HCS{woah.hexahue.adalah.alfabet.berwarna.c0y}`

Wish me luck…