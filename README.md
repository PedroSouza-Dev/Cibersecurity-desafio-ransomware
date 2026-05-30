# Cibersecurity-desafio-ransomware

# 🛡️ Simulador de Ransomware com Criptografia AES

Este projeto foi desenvolvido como um exercício prático durante um Bootcamp de Cibersegurança. O objetivo principal é demonstrar, para fins estritamente educacionais e de estudo de malware, como funciona o processo de cifragem e decifragem de arquivos utilizando criptografia simétrica.

> **⚠️ Aviso Importante:** Este código foi criado exclusivamente para fins didáticos e laboratoriais em ambientes controlados. O uso de mecanismos de criptografia para bloquear dados sem consentimento é ilegal e prejudicial.

---

## 🚀 Como Funciona o Projeto

O projeto simula a lógica básica de um *ransomware* (criptografador) e sua respectiva ferramenta de recuperação (descriptografador). Ele utiliza a biblioteca `pyaes` com o algoritmo **AES (Advanced Encryption Standard)** no modo **CTR (Counter)**.

### Cenário de Teste:
1. Um arquivo original chamado `teste.txt` contendo o texto `"Este arquivo esta legivel"` é criado no diretório.
2. O script de criptografia entra em ação, codifica o arquivo e altera sua extensão.
3. O script de descriptografia reverte o processo, trazendo o arquivo original de volta.

---

## 🛠️ Estrutura e Passo a Passo dos Scripts

### 1. Criptografador (`encrypter.py`)
Este script é responsável por simular o "ataque", tornando o arquivo inacessível.

* **Leitura dos Dados:** O script abre o arquivo alvo (`teste.txt`) em modo de leitura binária (`rb`) e armazena seu conteúdo na memória.
* **Destruição do Original:** O arquivo original é deletado do sistema usando `os.remove()`.
* **Inicialização da Chave:** É definida uma chave simétrica de 16 bytes (`b"testeransomwares"`).
* **Cifragem:** Utilizando o modo AES-CTR, o conteúdo do arquivo é transformado em dados criptografados (ilegíveis).
* **Gravação do Arquivo Cifrado:** Um novo arquivo é gerado com a extensão customizada `.ransomwaretroll`, contendo os dados modificados.

### 2. Descriptografador (`decrypter.py`)
Este script simula a ação de recuperação dos dados (como a aplicação de um *decryptor* após a contenção do incidente).

* **Leitura do Arquivo Cifrado:** O script localiza e lê o arquivo modificado (`teste.txt.ransomwaretroll`).
* **Inversão com a Mesma Chave:** Utilizando a **mesma chave simétrica** (`b"testeransomwares"`), o AES em modo CTR processa os dados criptografados para reverter a operação.
* **Limpeza:** O arquivo criptografado é removido do sistema.
* **Restauração:** O arquivo original `teste.txt` é recriado e o texto original decodificado é gravado perfeitamente.

---

## 📦 Tecnologias Utilizadas

* **Python 3**
* **pyaes**: Biblioteca pura em Python para o algoritmo AES (fácil de implementar e excelente para fins educacionais).
* **os**: Módulo nativo do Python para manipulação de arquivos no sistema operacional.

---

## ⚙️ Como Executar o Laboratório

1. Certifique-se de ter o Python instalado.
2. Instale a biblioteca necessária:
   ```bash
   pip install pyaes
