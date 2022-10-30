# GmailPhisingWith2FA
## Disclaimer

A finalidade deste repositório é apenas educacional, não me responsabilizo pelo uso indevido que possa ser feito das ferramentas nele contidas.
Não sou um programador especialista, todo o código será otimizado e melhorado em versões futuras.

[POR]
Este repositório destina-se apenas a fins educacionais.
Não sou um desenvolvedor especialista, o código será aprimorado em outras versões.
  
    
_[ENG]  
This repository is meant for educational purposes only.  
I'm not an expert developer, the code will be improved in futher versions._

## Decripción
A autenticação de dois fatores ou verificação em duas etapas (2FA) é uma medida de proteção dos sistemas de autenticação que consiste em o usuário apresentar duas provas para provar que é quem diz ser. Neste caso, este repositório tem como objetivo demonstrar como os invasores conseguem burlar o 2FA para o sistema de autenticação do Gmail. Os dois fatores usados ​​neste caso são a senha e um código enviado para o celular do usuário.

[POR]
A autenticação de dois fatores (2FA) adiciona uma camada adicional de proteção nos sistemas de autenticação que consiste na comprovação de que o usuário mostra ser o usuário real. Este repositório visa demonstrar como os invasores podem contornar o 2FA para o sistema de autenticação do Gmail. Nesse caso, os dois fatores são a senha e um código enviado ao usuário móvel.

## Dependencias
- [Apache2](https://www.apache.org/)
- [Python](https://www.python.org/)
- [Selenium](https://www.seleniumhq.org/)

## O que o repositório inclui?
- **gmailPhising:** contém o código de autenticação da web do Gmail, incluindo os scripts que armazenam os dados na máquina atacante.

- **logingmail.py:** contém o código do script que inicia o navegador para fazer login se passando pela vítima, na máquina do invasor. Este script faz uso do [Selenium](https://www.seleniumhq.org/).

- **root.sh:** Este script é responsável por executar logingmail.py . Ele deve ser capaz de rodar como root para o usuário que serve a web (www-data). Isso é configurado no arquivo /etc/sudoers na máquina atacante, incluindo a seguinte linha:

```
www-data ALL=(user) NOPASSWD: pathtoscript/root.sh
```

_[ENG]_    
- _**gmailPhising:** contains the code of the gmail's authetication web._

- _**logingmail.py:** script for running the web browser "impersonating" the victim's login in the attacker's machine. This makes use of [Selenium](https://www.seleniumhq.org/)._

- _**root.sh:** this script running **logingmail.py**. Must be run as root for user www-data. This is configured in /etc/sudoers of the attacker's machine including the following:_

```
www-data ALL=(user) NOPASSWD: pathtoscript/root.sh
```

## Como iniciar

```
git clone https://github.com/Saddam171/Phising-do-Facebook.git
cd 2FAGmailPhising
pip install -r requirements.txt
chmod +x run.sh
chmod +x geckodriver
./run.sh
```

## Cenário
O invasor através de alguma das técnicas de hacking (dnsspoofing, ingeniería social, etc.) redirige a uma vítima que tem 2FA ativado na web que suplanta o Gmail. Uma vez que a víctima introduzca sua correo e contraste na página falsa, a máquina do invasor iniciará automaticamente o navegador, introduzindo na web real do Gmail as credenciais da víctima, enviando esto que a víctima recebe a mensagem com o código do 2FA . Quando a vítima recebe o código de introdução na página falsa e ao inserir a máquina do invasor obtendrá este código e completará o início da sessão na web natural do Gmail, obtendo assim o acesso à conta da vítima.

[POR]
O atacante usando técnicas de hacking (dnsspoofing, engenharia social, etc.) redireciona a vítima com 2FA ativo no gmail para web gmail falsa. Depois que a vítima fizer login na web falsa, a máquina do invasor executará um navegador da web e irá para o gmail original para fazer login com as credenciais da vítima. Isso fará com que o Gmail envie o código de validação para a vítima. Quando a vítima receber o código, ela o colocará na teia falsa. O invasor obterá o código e concluirá o log na web original do Gmail, obtendo acesso à conta da vítima.

![alt text](https://raw.githubusercontent.com/afernandezb92/2FAGmailPhising/master/gmailPhising2FA.PNG)

## POC
![alt text](https://i.imgur.com/H2Hi1JN.gif)


## Melhoras
- Incluir os últimos dígitos do número de telefone da vítima na página falsa de solicitação do código.
- Modificar o fluxo de ejecução para permitir distinguir o usuário tiene 2FA ou no.
- Validar entrada de dados.
- Ficha de log.
- Sanetizar as entradas de dados.

