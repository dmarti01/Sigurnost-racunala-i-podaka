# Prva Vježba

Na prvoj vježbi smo radili Man-in-the-middle attack, odnosno ARP spoofing. Napad smo testirali i realizirali u Docker mreži sa 3 Docker računala. Ta računala smo nazvali **station-1**, **station-2** i **evil-station**.

Prvo smo otvorili Windows terminal i u njoj Ubuntu terminal, nakon čega smo klonirali GitHub repozitorij komandom: **git clone [https://github.com/mcagalj/SRP-2021-22](https://github.com/mcagalj/SRP-2021-22)**.

Zatim smo ušli u arp-spoofing direktorij koji je sačinjen od skripti koje služe za pokretanje i zaustavljanje ovog napada (**start.sh** i **stop.sh**).

Nakon toga smo pokrenuli skriptu komandom **./start.sh** i poslije nje upisali komandu **docker ps** pomoću koje možemo vidjeti sva virtualna računala.

Zatim smo pomoću komandi **netcat -l -p 8080** i **netcat station-2 8080** uspostavili vezu između **station-1** i **station-2**.

U **evil-station** smo pokrenuli ARP spoofing komandom **arpspoof -t 172.18.0.2 172.18.0.4**. 
U dupliciranom prozoru smo u **evil-station** također pokrenuli **echo 0 > /proc/sys/net/ipv4/ip_forward**. Nakon toga smo pomoću alata **tcpdump** gledali poruke između virtualnih računala. Komanda je **tcpdump -i eth0 -XX**.

Ovime smo zaključili prvu vježbu.
