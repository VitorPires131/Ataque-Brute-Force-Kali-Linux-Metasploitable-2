Nessa atividade irei simular um ataque de intrusão utilizando os métodos, FTP, Web e SMB, utilizando o Kali Linux e o Metasploitable 2


Reconhecimento e Descoberta de Possíveis Alvos Fáceis e vulnerareis

<img width="1920" height="955" alt="VirtualBox_Kali Linux_08_11_2026_18_04_38" src="https://github.com/user-attachments/assets/c03c863f-d1f1-4a3c-9ad3-2ea4ac99fe1c" />

Aqui o atacante ao executar os comandos "ip a" e "nmap -sn 192.168.56.102/24" ele consegue ver quem esta conectado a mesma rede que ele e ve o ip do aparelho



Observar possíveis brechas e métodos de invasão na vitima

<img width="1920" height="955" alt="VirtualBox_Kali Linux_08_11_2026_18_46_00" src="https://github.com/user-attachments/assets/a6a884a7-0132-4b0d-a630-e2c08fd46960" />

Nessa etapa ao executar o comando "nmap -sV 192.168.56.101" o atacante analisa quais métodos de ataque ele pode realizar e cada codigo mostra a vunerabilidade e o tipo de ataque que ele pode fazer



Metodos para descobrir usuario e senha da vitima

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_27_00" src="https://github.com/user-attachments/assets/4c3a4fe1-d07c-4ddb-b1d9-aa286cfa4cf0" />

Ao executar o comando ftp junto com o ip da vitima, o Atacante pode tentar o login da maquina da vitima utilizando sua propria maquina, sem precisar mexer na maquina da vitima.




