Nessa atividade irei simular um ataque de intrusão utilizando os métodos, FTP, Web e SMB, utilizando o Kali Linux e o Metasploitable 2



Ataque FTP

<img width="1920" height="955" alt="VirtualBox_Kali Linux_08_11_2026_18_04_38" src="https://github.com/user-attachments/assets/c03c863f-d1f1-4a3c-9ad3-2ea4ac99fe1c" />

Aqui o atacante ao executar os comandos "ip a" e "nmap -sn 192.168.56.102/24" ele consegue ver quem esta conectado a mesma rede que ele e vê o ip do aparelho



Observar possíveis brechas e métodos de invasão na vitima

<img width="1920" height="955" alt="VirtualBox_Kali Linux_08_11_2026_18_46_00" src="https://github.com/user-attachments/assets/a6a884a7-0132-4b0d-a630-e2c08fd46960" />

Nessa etapa ao executar o comando "nmap -sV 192.168.56.101" o atacante analisa quais métodos de ataque ele pode realizar e cada código mostra a vulnerabilidade e o tipo de ataque que ele pode fazer



Metodos para descobrir usuario e senha da vitima

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_27_00" src="https://github.com/user-attachments/assets/4c3a4fe1-d07c-4ddb-b1d9-aa286cfa4cf0" />

Ao executar o comando ftp junto com o ip da vitima, o Atacante pode tentar o login da maquina da vitima utilizando sua própria maquina, sem precisar mexer na maquina da vitima.



Preparacão para usar o Medusa

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_30_32" src="https://github.com/user-attachments/assets/9a83a4fc-8213-40ed-b33e-59b53f9ff290" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_32_10" src="https://github.com/user-attachments/assets/42500fdc-75d0-45ea-9534-e1cdcca6abbb" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_32_26" src="https://github.com/user-attachments/assets/2eb3ffb5-f8f0-4c63-a53d-54501859cbc1" />

Ao executar os comandos "echo -e "user\nmsfadmin\nadmin\nroot" > users.txt" e "echo -e "123456\npassword\nqwerty\nmsfadmin" > pass.txt" o Atacante cria duas listas de usuário e senha para um ataque Força Bruta com FTP utilizando possíveis combinações que podem ser o login da maquina da vitima



Atacando com o Medusa

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_44_02" src="https://github.com/user-attachments/assets/65bb0b2f-71d6-43b7-af1a-5111afc82fac" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_45_19" src="https://github.com/user-attachments/assets/1e6aa4cf-4339-46b0-8593-928bc44a42b7" />

Ao executar o comando "medusa -h 192.168.56.101 -U users.txt -P pass.txt -M FTP -t 6" o Atacante fez um ataque Força Bruta com FTP e acaba descobrindo o login e senha da maquina da vitima

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_11_51_43" src="https://github.com/user-attachments/assets/171dc9cf-efaf-4003-a2bb-8506cd87be06" />

Podemos ver que o Atacante fez a conexão bem sucedida e se conectar no prompt do FTP da maquina da vitima.



Ataque Web DVWA

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_10_55" src="https://github.com/user-attachments/assets/40031a56-415b-42df-8b26-9765c02df55a" />

Aqui o Atacante consegue ver informações importantes na hora de realisar o ataque como o POST e GET.

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_21_33" src="https://github.com/user-attachments/assets/184f24c6-4ea3-4ca6-b567-328c0ad7d05e" />

e indo a aba Request ve os comandos que o site utiliza para realizar o login



Criando Wordlists

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_29_55" src="https://github.com/user-attachments/assets/64f608cc-a27e-435d-b18d-1d48860374b2" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_30_36" src="https://github.com/user-attachments/assets/77ebc410-81ed-48fe-96df-8fd772be617a" />

Repetindo o que ja fizemos no FTP porem agora para Ataque Web



Realizando o Ataque

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_47_40" src="https://github.com/user-attachments/assets/1f684695-d6b4-4734-b67b-b387261030ca" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_49_53" src="https://github.com/user-attachments/assets/90a3fb0b-4058-46d6-add6-dbb67852e192" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_12_50_05" src="https://github.com/user-attachments/assets/974851de-b0c5-43cb-8d68-61d729d17382" />

Ao utilizar o comando.
"medusa -h 192.168.56.101  -U users.txt -P pass.txt -M http \
-m PAGE:'/dvwa/login.php \
-m FORM:'username=^USER^7password=^PASS^7Login=Login' \
-m 'FAIL=Login failed -t 6"
o Medusa testa varias combinações de usario e senha e ao recer o Login failed o medusa reconhece que aquela combinação não é a correta até achar a que esta correta.
Nota que ao descobrir o Medusa coloca em primeiro a cobinação correta e lista as outras combinações como "Sucessfull".

<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_13_19_14" src="https://github.com/user-attachments/assets/4257acf0-b5d9-4354-bc92-4d079cc4a5d2" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_13_19_32" src="https://github.com/user-attachments/assets/8e04e4db-053f-480d-ba33-9e39d2fb9e5b" />
<img width="1920" height="955" alt="VirtualBox_Kali Linux_10_11_2026_13_19_42" src="https://github.com/user-attachments/assets/16189935-ddcc-4d34-a75b-e3448739f4bb" />

