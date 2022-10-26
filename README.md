# recovery-EFR32MG1P
Восстанавливаем прошивку и загрузчик зигби чипа EFR32MG1P232GG 
![photo_5350792393798040824_y](https://user-images.githubusercontent.com/64173457/178154977-d43715ed-315a-4875-97af-ff62c95684ac.jpg)

роутера perenio PEACG01:
![gate2](https://user-images.githubusercontent.com/64173457/178155032-c6265a91-f3a1-4aae-bbf3-1e087a20f179.jpg)

Понадобится st-link с aliexpress, типа такого:
![photo_5357544692272709244_y](https://user-images.githubusercontent.com/64173457/178154243-d957c86d-a2f5-4f4c-8bc7-958aa72321c5.jpg)

На плате, с обратной стороны выведены TP от чипа.
![photo_5354870873267485840_y](https://user-images.githubusercontent.com/64173457/178154269-3c7042e6-bbd5-4fa2-ad49-ece07a535b5c.jpg)

подпаиваем провода и подключаем подключаем к st-link.
![photo_5354870873267485841_y](https://user-images.githubusercontent.com/64173457/178154278-be01d4f7-4a3b-4a76-81da-0de9432d39ec.jpg)

GND->GNG, RST->RST, CLK->SWCLK, TMS->SWDIO
Будте аккуратны, не перегревайте плату, не дергайте за припаяные провода. Оторвав дорожки работать будет значительно сложнее.
Подключаем st-link к ПК и устанавливаем драйвера.
[EBlink-master_2.0.zip](https://github.com/esnet146/recovery-EFR32MG1P/files/9079472/EBlink-master_2.0.zip) [или тут](https://www.st.com/en/development-tools/stsw-link009.html)

Скачиваем прошивальщик с скриптами и прошивкой и распаковываем. 
[eblink.zip](https://github.com/esnet146/recovery-EFR32MG1P/files/9079484/eblink.zip) В [оигинале](https://www.embitz.org/) - кроссплатформенный, здесь win32 версия

Переходим в каталог с исполняемым файлом и прошиваем загрузчик:
`eblink.exe -I stlink,dr -S silabs-auto -P ../scripts/ -F erase,verify,run,file=BTL_STD_S1_256-COM_PA0-PA1-PD15.sre`

Прошивку:
`eblink.exe -I stlink,dr -S silabs-auto -P ../scripts/ -F verify,run,file=NCP_USW_115K2_S1_F256_678_PA0-PA1.srec`

Можно пользоватся.

ps
[ncp.zip](https://github.com/esnet146/recovery-EFR32MG1P/files/9868818/ncp.zip)
