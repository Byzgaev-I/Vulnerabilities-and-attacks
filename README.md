# Домашнее задание к занятию "`«Уязвимости и атаки на информационные системы»`" - `Бызгаев Александр`

---

### Задание 1

Скачайте и установите виртуальную машину Metasploitable.
Просканируйте эту виртуальную машину, используя nmap.
Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.
Ответьте на следующие вопросы:  

    Какие сетевые службы в ней разрешены?    
    Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)  
Приведите ответ в свободной форме.

### Решение:

Установил и просканировал: 

![image](https://github.com/Byzgaev-I/Vulnerabilities-and-attacks/blob/main/Metasploitable.png)

![image](https://github.com/Byzgaev-I/Vulnerabilities-and-attacks/blob/main/Metasploitable2.png)


По уязвимостям можно выделить следующие:
 
- vsftpd 2.3.4 https://www.exploit-db.com/exploits/49757
- GNU Classpath 0.97.2 https://www.exploit-db.com/exploits/32674
- ProFTPd 1.3 https://www.exploit-db.com/exploits/32798
- ISC BIND  https://www.exploit-db.com/exploits/40453

---

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.  
Запишите сеансы сканирования в Wireshark.  
Ответьте на следующие вопросы:  
    - Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?    
    - Как отвечает сервер?
    
Приведите ответ в свободной форме.

### Решение:

Эти режимы сканирования отличаются по способу, которым они взаимодействуют с портами на целевой машине, а также по типу сетевого трафика, который они генерируют. Вот как ведёт себя каждый из режимов сканирования и как на них может отвечать сервер:  

1. SYN сканирование (полуоткрытое сканирование или сканирование с использованием флага SYN):  

 - Трафик: Отправляет пакеты TCP с флагом SYN, пытаясь начать соединение с каждым портом.  
 - Ответ сервера:  
          - Открытый порт отвечает пакетом SYN-ACK, говоря о готовности установить соединение.  
          - Закрытый порт отвечает пакетом RST (reset), предотвращая установление соединения.  
- Nmap прекращает или завершает процесс рукопожатия, отправляя RST, если порт открыт. 

2. FIN сканирование:  

 - Трафик: Отправляет пакеты TCP с установленным FIN флагом, что обычно означает завершение соединения.  
 - Ответ сервера:  
          - По стандарту TCP, открытые порты игнорируют пакеты FIN в отсутствие активного соединения, и не отвечают на них.  
          - Закрытые порты должны отвечать пакетом RST.  

3. Xmas сканирование:

 - Трафик: Отправляет пакеты TCP с флагами FIN, PSH и URG, что создаёт "освещённый" или "рождественский" пакет (отсюда и название).  
 - Ответ сервера:  
        - Аналогично с FIN сканированием, открытые порты обычно не отвечают на такие пакеты.  
 - Закрытые порты отвечают пакетом RST.  

4. UDP сканирование:  

 - Трафик: Отправляет UDP пакеты на разные порты.  
 - Ответ сервера:  
        - Если порт UDP открыт и прослушивается, то сервер может не ответить вообще, либо ответить со специфическими для приложения данными.  
        - Если UDP порт закрыт, то сервер отвечает ICMP пакетом "port unreachable".  

Как мы видим, основные различия между этими режимами связаны с типами флагов, устанавливаемых в заголовке TCP, и с поведением сервера при получении этих пакетов.   
SYN сканирование является наиболее спокойным и надежным методом для определения состояния портов, в то время как остальные методы могут быть неэффективны против современных межсетевых экранов и систем обнаружения вторжений, которые могут обнаружить и заблокировать такие сканирования.   
UDP сканирование отличается от TCP сканирования тем, что использует протокол UDP вместо TCP и в некоторых случаях может требовать больше времени для получения ответов, так как UDP — это протокол без установления соединения.
