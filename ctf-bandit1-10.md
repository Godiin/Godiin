# 🚩 OverTheWire: Bandit (Levels 0 → 10)

Esta é a documentação das soluções dos níveis 0 a 10 do WarGame **Bandit** da plataforma OverTheWire. O objetivo principal deste desafio é praticar comandos básicos de Linux e conceitos de segurança em servidores SSH.

---

## 🗂️ Tabela de Conteúdos
* [Level 0 → Level 1](#level-0--level-1)
* [Level 1 → Level 2](#level-1--level-2)
* [Level 2 → Level 3](#level-2--level-3)
* [Level 3 → Level 4](#level-3--level-4)
* [Level 4 → Level 5](#level-4--level-5)
* [Level 5 → Level 6](#level-5--level-6)
* [Level 6 → Level 7](#level-6--level-7)
* [Level 7 → Level 8](#level-7--level-8)
* [Level 8 → Level 9](#level-8--level-9)
* [Level 9 → Level 10](#level-9--level-10)

---

### Level 0 → Level 1
* **Conceito:** Acesso inicial ao servidor via SSH utilizando a senha padrão.
* **Senha obtida:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`
* **Comando para o próximo nível:**
  ```bash
    ssh bandit1@bandit.labs.overthewire.org -p 2220

### Level 1 → Level 2
* **Conceito:** Leitura de arquivos com nomes especiais (traço -). Para ler, precisamos especificar o caminho relativo ./-.
* **Senha obtida:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`
* **Comandos utilizados:**
  ```Bash
    cat ./-
  
### Level 2 → Level 3
* **Conceito:** Leitura de arquivos que possuem espaços no nome. Deve-se usar aspas ou escapar os espaços com barra invertida \.
* **Senha obtida:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`
* **Comandos utilizados:**
  ```Bash
    cat "spaces in this filename"

### Level 3 → Level 4
* **Conceito:** Listagem de arquivos ocultos (arquivos que começam com ponto .) utilizando a flag -a.
* **Senha obtida:** `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`
* **Comandos utilizados:**
  ```Bash
    ls -a inhere/
    cat inhere/.hidden

### Level 4 → Level 5
* **Conceito:** Identificação do tipo de arquivo usando o comando file. O objetivo era encontrar o único arquivo legível por humanos (ASCII text).
* **Comandos utilizados:**
* **Senha obtida:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`
  ```Bash
    file ./*
    cat ./-file07

### Level 5 → Level 6
* **Conceito:** Uso avançado do comando find para filtrar por propriedades específicas: tamanho (1033 bytes), tipo (arquivo) e não-executável.
* **Senha obtida:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`
* **Comandos utilizados:**
  ```Bash
    find . -type f -size 1033c ! -executable
    file ./inhere/maybehere07/.file2
    cat ./inhere/maybehere07/.file2

### Level 6 → Level 7
* **Conceito:** Busca de arquivos em todo o sistema (/) filtrando por usuário, grupo e tamanho, redirecionando erros (2> /dev/null) para limpar a saída.
* **Senha obtida:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`
* **Comandos utilizados:**
  ```Bash
    find / -user bandit7 -group bandit6 -size 33c 2> /dev/null

### Level 7 → Level 8
* **Conceito:** Filtragem de conteúdo dentro de um arquivo de texto usando o comando grep.
* **Senha obtida:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`
* **Comandos utilizados:**
  ```Bash
    grep "millionth" data.txt

### Level 8 → Level 9
* **Conceito:** Identificação de uma linha única em um arquivo de texto. O comando uniq exige que a entrada esteja ordenada (sort).
* **Senha obtida:** `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`
* **Comandos utilizados:**
  ```Bash
    sort data.txt | uniq -u

### Level 9 → Level 10
* **Conceito:** Extração de strings legíveis por humanos de dentro de um arquivo binário/dados e filtragem subsequente.
* **Senha obtida:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`
* **Comandos utilizados:**
  ```Bash
    strings data.txt | grep "="

### Level 10 → Level 11
* **Conceito:** Decodificação de dados que foram codificados em formato Base64.
* **Senha obtida (Bandit 11):** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`
* **Comandos utilizados:**
  ```Bash
    base64 -d data.txt

📝 Nota: Esta documentação serve como registro de aprendizado e progressão nos desafios de Linux/Hacking da plataforma OverTheWire.
