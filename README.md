# MyHackTool — Hack Toolkit

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python Version">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/Security-Recon-red?style=for-the-badge" alt="Topic">
</p>

O **MyHackTool** é um script em Python desenvolvido para centralizar duas etapas essenciais da fase de reconhecimento (*recon*) em auditorias de segurança e testes de intrusão: a **enumeração de subdomínios via DNS** e a **varredura de diretórios via HTTP/HTTPS**.

A ferramenta utiliza técnicas para minimizar falsos positivos, possui cabeçalhos realistas para evitar bloqueios automáticos simples e suporta o uso de dicionários (*wordlists*) totalmente customizados através de uma interface de linha de comando robusta.

---

## ✨ Funcionalidades Principais

* 📡 **Módulo DNS (`--sub`):** Enumeração rápida de subdomínios testando resoluções de IP diretamente via socket.
* 🌐 **Módulo HTTP (`--dir`):** Brute force de diretórios web com análise inteligente de respostas.
* 🕵️‍♂️ **Evasion Simples:** Cabeçalhos HTTP (`Headers`) altamente realistas, mimetizando o comportamento do Google Chrome moderno no Windows 11 para contornar assinaturas estáticas básicas.
* 🎯 **Filtro de Custom 404:** Análise dinâmica de *baseline* que identifica e sinaliza páginas de erro 404 personalizadas ocultas sob códigos de status irregulares.
* ⚙️ **Interface Amigável:** Integração completa com o `argparse`, oferecendo tratamento flexível de argumentos e menu de ajuda integrado no terminal.

---

## 🛠️ Pré-requisitos & Instalação

Antes de executar, certifique-se de que possui o Python Versão 3 instalado e a biblioteca `requests` atualizada.

1. **Clonar o Repositório:**
   ```bash
   git clone https://github.com/Johny-py778/myhacktool.git
   cd myhacktool
   ```

2. **Instalar Dependências:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Wordlists:**
   Certifique-se de ter as listas de palavras necessárias no diretório do script ou passe o caminho delas nos parâmetros. Por padrão, o script procura por:
   * `common.txt` (Para diretórios)
   * `subdomains-10000.txt` (Para subdomínios)

---

##  Como Utilizar

A sintaxe aceita tanto o alvo quanto as opções em posições flexíveis. Para consultar o manual integrado, execute sem argumentos:

```bash
python myhacktool.py -h
```

### Exemplos Práticos:

#### 1. Varredura de Subdomínios (Modo DNS)
Procura subdomínios válidos associados ao domínio alvo usando a wordlist padrão:
```bash
python myhacktool.py --sub exemplo.com 
```

#### 2. Varredura de Diretórios Web (Modo HTTP)
Descobre diretórios e arquivos em uma aplicação web com suporte à detecção de tamanho de página:
```bash
python myhacktool.py --dir https://exemplo.com 
```
## ou 
```bash
python myhacktool.py --dir exemplo.com
```

#### 3. Utilizando Wordlist Customizada (`-w` / `--wordlist`)
Você pode especificar sua própria lista de termos em qualquer um dos modos:
```bash
python myhacktool.py  --sub -w /caminho/minha_lista_sub.txt exemplo.com
```

---

## 📊 Arquitetura do Output

O script possui um sistema de logs em tempo real para facilitar a leitura dos resultados no terminal:

* `[+]` **Status de Sucesso:** Indica um subdomínio resolvido com sucesso ou uma página HTTP válida (Status 200, 301, 302, 403).
* `[!]` **Alerta Importante:** Indica possíveis páginas 404 customizadas (quando o tamanho da resposta diverge drasticamente do comportamento padrão do host).
* `[-]` **Erros de Conexão:** Registra falhas na resolução de hosts específicos sem interromper o loop principal.

---

## 🔏 Aviso Legal (Disclaimer)

> [!WARNING]
> **Uso Exclusivamente Educacional e Autorizado:** Esta ferramenta foi criada exclusivamente para fins didáticos, laboratoriais e para apoiar profissionais de segurança em auditorias devidamente autorizadas. O uso deste script contra alvos sem a expressa permissão prévia do proprietário é estritamente proibido e constitui uma violação legal. O desenvolvedor não se responsabiliza por quaisquer danos ou uso indevido deste software.

---
# Markdown
## 📄 Licença

Este projeto está licenciado sob a **Licença Pública Geral GNU v3.0 (GPLv3)**.

### Resumo dos Termos:

* **Permissões:** Uso comercial, modificação, distribuição e patentes.
* **Condições:** O código-fonte original e todas as modificações devem ser disponibilizados publicamente sob a mesma licença GPLv3. As alterações feitas no código devem ser documentadas.
* **Limitações:** O software é fornecido "como está", sem garantias de qualquer tipo por parte do autor.

Para ler a licença completa e detalhada, consulte o ficheiro [LICENSE]

⭐ Se este projeto te ajudou em seus estudos de segurança, considere deixar uma estrela no repositório!
