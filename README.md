<p align="center">
    <img src="https://i.imgur.com/xsy6BHJ.png"/> 
</p>
<p align="center">
    Guia para "converter" o tráfego do cliente OpenConnect para um proxy.    
</p>
<br>

### Motivação 
---
Fazer um bypass nas regras da vpn, Exemplo: Discord, Linkedin, Spotify, Youtube. E também não queria routear todo o meu tráfego para a vpn.

<br>

### Bypass
---
Você só vai precisar instalar o [ocproxy](https://github.com/cernekee/ocproxy), para "converter" o tráfego para proxy socks5. 
<br> 
<br> 

*Instalação ocproxy em distribuições baseadas no* **Debian** 
``` bash
sudo apt install ocproxy
```

---
Exemplo da execução do OpenConnect com **ocproxy**
``` bash
sudo openconnect --protocol=gp exemplo.exemplo.br --script-tun --script "ocproxy -D 9052"
```

Pronto agora o sua vpn se "transformou" em um **proxy socks5** na porta **9052**

---
<br>

Você pode usar o [foxyproxy](https://getfoxyproxy.org/) para configurar seu navegador, também pode usar o [proxychains](http://proxychains.sourceforge.net/), para executar aplicações que não possuem configuração padrão para especificar um proxy.



*Instalação proxychains em distribuições baseadas no* **Debian** 
``` bash
sudo apt install proxychains proxychains4
```
<br>

*Configurando o* **proxychains** *para apontar porta especificada no ocproxy*, para configurar o **proxychains**, é necessário especificar o tipo de proxy, host, porta e credenciais, no arquivo de configuração **/etc/proxychains.conf**
<br>
<br>

*No nosso caso somente precisamos especificar o tipo, host e porta.*
```bash 
[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
#socks4 	127.0.0.1 9050
socks5 	127.0.0.1 9052 
```
*Utilização, segue o usage do* **proxychains**
```bash
Usage:	proxychains program_name [arguments]
```

*Exemplo de uso do* **proxychains**

```bash
proxychains curl exemplo.exemplo.br
```

<br>
<br>

---
### Conclusão
O bypass é importante, porque alem de conseguir acessar aplicações bloqueadas, você evita de rotear todo seu tráfego, assim adquirindo mais privacidade.
