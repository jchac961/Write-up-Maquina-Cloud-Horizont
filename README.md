<img width="660" height="249" alt="Captura de pantalla 2026-07-05 232335" src="https://github.com/user-attachments/assets/6c6c973d-34a7-4c78-9174-6c8a08be4093" />

# Write-up-Maquina-Cloud-Horizont

Maquina de www.whoami-labs.com

Inicio de la maquina vulnerable

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 215836" src="https://github.com/user-attachments/assets/d7c921af-359f-4bdf-9e05-8ee1d37a36bb" />

# RECONOCIMIENTO

Una vez iniciada la maquina vulnerable realizamos un escaneo de puertos utilizando la herramienta nmap

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 220020" src="https://github.com/user-attachments/assets/0943c086-c5be-423e-b49a-ae26d08edc0e" />
Dentro de los puertos encontrados tenemos 
Puerto #21 corriendo un servicio vsftpd 3.0.5
Puerto #22 corriendo un servicio OpenSSH 8.9p1
Puerto #139 corriendo un servicio Samba smbd 4
Puerto #145 corriendo un servicio Samba smbd 4
Puerto #8080 corriendo un servicio SimpleHTTPServer 0.6 

En vista que teniamos un hhtp en el puerto #8080 procedimos a verificar en un navegador que contenia el mismo

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 220410" src="https://github.com/user-attachments/assets/d850b7af-f415-4e57-9883-e966d0a10995" />

Luego de esto verificamos si obteniamos información por el servicio samba, pero no nos dio nada de importancia

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 220630" src="https://github.com/user-attachments/assets/84f08e5e-6339-41c8-93f0-3591689efc8c" />

Ingresamos utilizando el servicio ftp con el usuario anonymous a ver si encontrabamos algo de importancia, y dentro de la maqina encontramos un directorio llamado uploads por lo que procedimos a revisarlo pero no contenia nada en su interior

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 220255" src="https://github.com/user-attachments/assets/dd9ee7ca-7549-4bb3-82c1-25f012c78f49" />

Cree un aerchivo y lo subi a ver si de alguna manera podia ejecutarlo, pero cuando lo liste por primera vez me aparecio, pero luego lo volvi a listar y el mismo se borro

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 230619" src="https://github.com/user-attachments/assets/d79b2066-879c-45ab-90d1-25b9455621f1" />

Me toco investigar un poco sobre el tema ya que anteriormente no habia visto esto

<img width="1426" height="391" alt="Captura de pantalla 2026-07-05 231436" src="https://github.com/user-attachments/assets/bdd1fb1b-824d-4f67-bc6c-8f29a4e29dbb" />

Ya comprendiendo que pasaba con esta maquina procedi a crear un archivo que contuviera una reverse shell, mediante un script de bash el cual una vez subido a la maquina en cuanto debiera ejecutarse la tarea me daria de vuelta la reverse shell a mi maquina kali

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 230947" src="https://github.com/user-attachments/assets/823bb348-7962-425c-8f96-f2091c0b95c5" />

# EXPLOTACION  

Subi el archivo

<img width="1920" height="220" alt="Captura de pantalla 2026-07-05 231015" src="https://github.com/user-attachments/assets/600513a2-b63b-4a79-8eb0-7082fb996f59" />

Puse mi kali en modo escucha

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 230632" src="https://github.com/user-attachments/assets/72740cd3-6045-4b2a-881f-ffab83aa115c" />

y obtuve la reverse shell

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 231023" src="https://github.com/user-attachments/assets/acf92d91-4b79-47c2-841d-574f6736958c" />

# ESCALADA DE PRIVILEGIOS

Ya dentro de la maquina verifique los archivos a ver si encontraba alguno de importancia pero no, asi que procedi a listar los binarios en busca de alguno con mala configuración y encontre el llamado find que anteriormente he podido utilizar para ingresar a maquinas

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 231103" src="https://github.com/user-attachments/assets/5d179405-1863-4c23-9fe9-d09bd7c1885d" />

Lo ejecute y tuve acceso a la máquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 231159" src="https://github.com/user-attachments/assets/2148145e-b5ef-4d87-bc67-ca9e1b7629fa" />

# RESULTADOS

Busque la flag

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 231224" src="https://github.com/user-attachments/assets/873c643c-68e1-46e7-a13c-499233eeb24e" />

Powned

<img width="1920" height="1140" alt="Captura de pantalla 2026-07-05 231925" src="https://github.com/user-attachments/assets/9055a492-0278-4c25-b06b-70ddaf61cd96" />

Listo

<img width="2688" height="1596" alt="Gemini_Generated_Image_8i02238i02238i02" src="https://github.com/user-attachments/assets/d370b5c5-144e-461f-9aa7-9c8701bfd919" />

