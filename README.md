# Домашнее задание к занятию «Уязвимости и атаки на информационные системы»

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
#### Ответ:

- Список открытых служб:

PORT     STATE SERVICE

21/tcp   open  ftp

22/tcp   open  ssh

23/tcp   open  telnet

25/tcp   open  smtp

53/tcp   open  domain

80/tcp   open  http

111/tcp  open  rpcbind

139/tcp  open  netbios-ssn

445/tcp  open  microsoft-ds

512/tcp  open  exec

513/tcp  open  login

514/tcp  open  shell

1099/tcp open  rmiregistry

1524/tcp open  ingreslock

2049/tcp open  nfs

2121/tcp open  ccproxy-ftp

3306/tcp open  mysql

5432/tcp open  postgresql

5900/tcp open  vnc

6000/tcp open  X11

6667/tcp open  irc

8009/tcp open  ajp13

8180/tcp open  unknown



- Одни из обнаруженных уязвимостей:

vsftpd 2.3.4 - Backdoor Command Execution https://www.exploit-db.com/exploits/17491

TelnetD encrypt_keyid - Function Pointer Overwrite  https://www.exploit-db.com/exploits/18280

OpenSSH < 7.4 - agent Protocol Arbitrary Library Loading https://www.exploit-db.com/exploits/40963

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

#### Ответ:

- Syn сканирование посылает хосту пакет с флагом SYN и ожидает ответ от хоста: Если SYN/ACK - порт открыт, если RST - порт закрыт

- Fin сканирование посылает хосту пакет с флагом FIN и ожидает ответ от хоста: если RST - порт закрыт, если хост проигнорировал пакет, то открыт

- Xmas сканирование посылает хосту пакет с флагами FIN, PSH и URG и ожидает ответ от хоста: если RST - порт закрыт, если хост проигнорировал пакет, то открыт

- UDP сканирование посылает udp пакет и ожидает ответ от хоста: если приходит ошибка ICMP port unreachable (тип 3, код 3) — порт закрыт, если сервис ответил своим пакетом - порт открыт

Первые пакеты SYN сканирования в Wireshark:

<img width="1138" height="636" alt="image" src="https://github.com/user-attachments/assets/d12f7a7f-f3a4-4c5e-8ba2-a3acebcd9819" />

Первые пакеты FIN сканирования в Wireshark:

<img width="989" height="637" alt="image" src="https://github.com/user-attachments/assets/3c6ae1f9-416c-4de9-a1e1-d3f03b711ef1" />

Первые пакеты Xmas сканирования в Wireshark:

<img width="961" height="628" alt="image" src="https://github.com/user-attachments/assets/a5a8e2ce-9a40-4183-ae5b-41e8b2141c24" />

Первые пакеты UDP сканирования в Wireshark:

<img width="874" height="631" alt="image" src="https://github.com/user-attachments/assets/8ad20524-9009-470c-95e2-4a563ecd951b" />
