Задание № 1
Чтобы провести аудит безопасности системы, вам необходимо установить специальное программное обеспечение:
если у вас установлена Windows OS, зайдите на сайт ФСТЭК России 
и скачайте программное обеспечение ScanOVAL и базу уязвимостей. В случае возникновения вопросов по программному обеспечению воспользуйтесь инструкцией по эксплуатации оператором программного обеспечения;
если у вас установлен Linux OS, скачайте Lynis, база уязвимостей включена в ПО.
4.	Проведите аудит системы по примеру из лекции.
5.	Какие уязвимости вы нашли — их точно будет не менее 5. Какие рекомендации вы можете дать по их устранению?
6.	Сделайте выводы по степени защищённости операционной системы.

Аудит системы показал, что уровень защиты операционной системы низкий. Выявлено более 10 уязвимостей критического уровня связанных с установкой нелицензированного ПО.

Задание № 2
1.	Скачайте и установите программное обеспечение nmap (zenmap).
2.	Проведите анализ точки доступа, установленной у вас дома. Для этого определите адрес шлюза по умолчанию командой ipconfig для Windows и ip route для Linux.
3.	Выполните проверку доступности шлюза по умолчанию командой ping: ping ‘ip address default gate’ (например, ping 192.168.0.1).
4.	Запустите программу nmap (zenmap) и выполните команду nmap -sV ‘ip address default gate’ -p-. Здесь ‘ip address default gate’ — ping 192.168.0.1 из примера выше.
5.	Дайте ответ на следующие вопросы:
•	Кто производитель оборудования?
•	Какая операционная система установлена на устройстве?
•	Сколько портов открыто на устройстве?
•	Какие сервисы доступны?
•	Есть ли опасные сервисы? Как узнать: скопируйте название службы и её версию, проверьте в поисковой системе.
6.	Сделайте выводы по степени защищённости вашего устройства.

1)	Производитель оборудования LLC NTC Rotek
2)	Операционная система на устройстве Linux 3.2 - 4.14
3)	4 открытых порта
4)	Доступные сервисы: tcpwrapped (неизвестен), dnsmasq 2.87, Boa HTTPd 0.93.15, MiniUPnP
21/tcp    filtered ftp
23/tcp    filtered telnet
53/tcp    open     domain     dnsmasq 2.87
80/tcp    open     http       Boa HTTPd 0.93.15
|_http-server-header: Boa/0.93.15
5355/tcp  open     tcpwrapped
7547/tcp  filtered cwmp
49152/tcp open     upnp       MiniUPnP
Опасных нет. Под вопросом tcpwrapped «В общем, tcpwrapped — это спецправило Nmap, и срабатывает оно тогда, когда сервер обрывает подключение до того, как данные были отправлены.» xaker.ru


Задание 3. Анализ сетевого трафика (задание со * повышенной сложности)
1.	Установите Wireshark. Инструмент понадобится для сбора сетевого трафика и последующего его анализа.
2.	После установки Wireshark перезапустите систему.
3.	После перезагрузки в начале работы запустите Wireshark.
4.	Включите сбор информации через сетевой интерфейс и приступите к работе.
5.	Зайдите на любые сайты, посмотрите различные ресурсы. Собирайте информацию не более 5 минут, после чего отключите сбор информации и сохраните лог пакетов.
6.	При работе с Wireshark опирайтесь на инструкцию.
7.	Приступите к анализу:
•	Какие пакеты генерируются в вашей сети?
•	Что вы можете сказать о содержимом пакетов?
•	Какая подозрительная информация вам встречалась?
8.	Сделайте выводы.

1)	Генерируются следующие протоколы: ARP, DNS, SSDP, TCP, HTTP и другие
2)	При проверке обновлении OS Windows

- Microsoft-CryptoAPI/10.0 HTTP GET на сервис OCSP (проверка протокола (крипто))
Ответ OCSP Response

- Большое количество входящих пакетов одного размера протокол TCP
IP 37.9.117.6
При сканировании Zenmap: strm-m9-15.strm.yandex.net
Вывод: потоковое видео сервис Кинопоиск
По данным «СПАРК-Интерфакс», ООО «Кинопоиск» на 100% принадлежит МКПАО «Яндекс» через ООО «Технояк»
3)	Подозрительная информация: нет