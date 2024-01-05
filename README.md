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

