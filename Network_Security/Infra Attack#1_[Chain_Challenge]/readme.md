![image-20240415220928914](./assets/image-20240415220928914.png)

Challenge contain 1 pcap file.

![image-20240415220948577](./assets/image-20240415220948577.png)

For overview of activities, I usually upload the pcap file to online pcap analyzer.

![image-20240415221127457](./assets/image-20240415221127457.png)

![image-20240415221240674](./assets/image-20240415221240674.png)

I saw the Kerberos ticket request. So I assume that malicious activities is kerberoasting or AS-REP Roasting.

Let's drill down to confirm our hypothesis.

```
kerberos or ldap
```

![image-20240415222017674](./assets/image-20240415222017674.png)

https://jsecurity101.medium.com/ioc-differences-between-kerberoasting-and-as-rep-roasting-4ae179cdf9ec

https://www.netwrix.com/cracking_kerberos_tgs_tickets_using_kerberoasting.html

![image-20240415235528860](./assets/image-20240415235528860.png)

TGS-Ticket request

![image-20240415222438509](./assets/image-20240415222438509.png)

TGS-Ticket granted

![image-20240415222333416](./assets/image-20240415222333416.png)

![image-20240415232606838](./assets/image-20240415232606838.png)

![image-20240415233123531](./assets/image-20240415233123531.png)

![image-20240415233420384](./assets/image-20240415233420384.png)

![image-20240415233944339](./assets/image-20240415233944339.png)

Let's breakdown what I gain from analysis.

1.Attacker trying to enumeration on DC server to find account associated with SPN record.

2.This is not AS-REP Roasting attack. Because Kerberos pre-authentication was required. And there should be a TGT-REQ/TGT-REP.

3.It's likely to be Kerberoasting attack, because DC server is authorizing the user through AS-REQ/AS-REP, then sending service ticket that was requested TGS-REQ/TGS-REP.

4.There was a Kerberos V5 TGS-REP etype 23 which known to  offline brute force attack with hashcat.

| Kerberoasting                                                | AS-REP Roasting                                              | PCAP file                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Attacker trying to find account associated with Service Principal Names (SPN) | Same with Kerberoasting.                                     | Attacker trying to find account associated with Service Principal Names (SPN) |
| AS-REQ/AS-REP Then TGS-REQ/TGS-REP                           | Only AS-REQ/AS-REP, Requests a Kerberos Authentication Ticket (TGT) | AS-REQ/AS-REP Then TGS-REQ/TGS-REP. There is no TGT-REQ/TGT-REP |
| -                                                            | Do not require Kerberos pre-authentication                   | Require Kerberos pre-authentication                          |
| Kerberos V5 TGS-REP etype 23                                 | Kerberos V5 AS-REP etype 18                                  | Have both                                                    |


```
network{kerberoasting}
```

