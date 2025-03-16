# 🚀 Servidor Rápido com Node.js e Logs Automáticos

Este projeto demonstra como criar um **servidor simples** utilizando **Node.js**.  
Ele exibe informações sobre o **sistema operacional** e **hostname** do servidor.  
Além disso, ele **registra automaticamente os acessos** em um arquivo de log (`log.txt`), anotando a **data e hora** de cada visita.

---

## 🛠 **Tecnologias Utilizadas**
- **Node.js** 📦 (JavaScript no backend)
- **Módulo `http`** para criar o servidor 🌐
- **Módulo `fs`** para manipulação de arquivos 📄
- **Módulo `os`** para capturar informações do sistema 💻

---

## ⚡ **Como funciona?**
1️⃣ O servidor inicia na **porta 3000** e responde com um HTML básico exibindo:
   - O **Sistema Operacional** do servidor.
   - O **Hostname** da máquina.

2️⃣ Cada acesso à página gera um **registro no arquivo `log.txt`**, armazenando a data e hora da visita.

---

## ▶️ **Como criar, configurar e rodar o projeto**

### 1️⃣ **Instale o Node.js (se ainda não tiver)**
Verifique se o Node.js está instalado no seu sistema:
```sh
node -v

## 2️⃣ Crie e configure o projeto

### 🔹 Crie um diretório e entre nele:
mkdir servidor-node
cd servidor-node
🔹 Inicie um projeto Node.js:
npm init -y
   Isso criará o arquivo package.json, que gerencia as configurações do projeto.

🔹 Crie o arquivo index.js
----------------------------------------------------------------------------------------
Adicione o código no arquivo:
const http = require("http");
const os = require("os");
const fs = require("fs");

const savelog = () => {
    fs.appendFileSync('log.txt', `Acesso efetuado em ${new Date()}\n`);
};

http.createServer((req, res) => {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.write("<html><body>");
    res.write("<h1>Servidor</h1>");
    res.write(`Plataforma: ${os.platform()}<br/> `);
    res.write(`Endereço: ${os.hostname()}<br/> `);
    res.write("</body></html>");
    res.end();
    savelog();
}).listen(3000);

console.log("Servidor executando na porta 3000");
3️⃣ Rodar o servidor
No terminal, execute:
node index.js

Se tudo estiver correto, verá a mensagem:
Servidor executando na porta 3000


----------------------------------------------------------------------------------------
Agora, acesse no navegador:

http://localhost:3000

📜 Exemplo de Log Gerado (log.txt)
Cada vez que o servidor recebe uma requisição, ele adiciona uma linha ao arquivo log.txt:

Acesso efetuado em Sat Mar 15 2025 19:41:39 GMT-0300
Acesso efetuado em Sat Mar 15 2025 19:41:40 GMT-0300
Acesso efetuado em Sat Mar 15 2025 19:45:59 GMT-0300






