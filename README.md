# Comandos-Sort-no-Linux
Este repositório contém uma documentação prática sobre o comando sort no Linux, utilizado para ordenação e filtragem de dados em arquivos de texto. São abordadas suas principais opções, exemplos de uso e dicas para aplicar ordenações alfabéticas, numéricas e personalizadas em diferentes contextos.

# 🐧 Guia para Iniciantes — Comandos de Ordenação e Filtragem no Linux

![Linux Logo](https://upload.wikimedia.org/wikipedia/commons/3/35/Tux.svg)

> Aprenda os comandos essenciais para **ordenar, filtrar e manipular textos no Linux**.  
> Este guia foi feito para quem está começando e quer dominar o terminal passo a passo. 🚀

---

## 📘 O que são comandos de ordenação e filtragem?

No Linux, esses comandos permitem **analisar, organizar e limpar dados** diretamente pelo terminal, sem precisar abrir planilhas ou editores de texto.

Eles são usados para:
- 🔍 Encontrar informações específicas
- 🧹 Remover repetições
- 📊 Ordenar e filtrar dados
- ⚡ Processar arquivos de forma rápida

---

## ⚙️ 1. `sort` — Ordenar Linhas

O comando **`sort`** serve para colocar as linhas de um arquivo em **ordem alfabética ou numérica**.

### 🧠 Como funciona:
Ele lê um arquivo e mostra as linhas em ordem crescente (A–Z, 0–9).

### 📌 Sintaxe:
```bash
sort [opções] nome_do_arquivo
💡 Exemplos:
bash
Copiar código
sort nomes.txt             # Ordena em ordem alfabética
sort -r nomes.txt          # Ordem reversa (Z–A)
sort -n numeros.txt        # Ordena numericamente
sort -k2 arquivo.txt       # Ordena pela 2ª coluna
🔸 Dica: o sort não muda o arquivo original.
Use > para salvar o resultado em outro arquivo:

bash
Copiar código
sort nomes.txt > nomes_ordenados.txt
🔁 2. uniq — Remover Linhas Duplicadas
O uniq remove linhas repetidas consecutivas.

⚠️ Importante: o arquivo precisa estar ordenado antes de usar uniq, senão ele não detecta duplicatas que estão em posições diferentes.

📌 Sintaxe:
bash
Copiar código
uniq [opções] arquivo
💡 Exemplos:
bash
Copiar código
sort nomes.txt | uniq        # Remove duplicadas
uniq -c nomes.txt            # Mostra quantas vezes cada linha aparece
uniq -d nomes.txt            # Mostra apenas as duplicadas
🔍 3. grep — Filtrar Linhas por Palavra ou Padrão
O grep é usado para procurar textos dentro de arquivos.
É ótimo para encontrar palavras, frases ou padrões.

📌 Sintaxe:
bash
Copiar código
grep [opções] "palavra" arquivo
💡 Exemplos:
bash
Copiar código
grep "Maria" nomes.txt           # Mostra linhas que contêm "Maria"
grep -i "maria" nomes.txt        # Ignora maiúsculas/minúsculas
grep -v "Maria" nomes.txt        # Exclui linhas com "Maria"
grep -r "erro" /var/log          # Procura "erro" dentro de várias pastas
💬 Dica: você pode combinar com outros comandos:

bash
Copiar código
cat log.txt | grep "falha" | sort | uniq -c
✂️ 4. cut — Cortar Colunas Específicas
O cut serve para pegar partes específicas de cada linha, como colunas de uma tabela.

📌 Sintaxe:
bash
Copiar código
cut [opções] arquivo
💡 Exemplos:
bash
Copiar código
cut -f1 nomes.txt               # Mostra a primeira coluna
cut -d',' -f2 arquivo.csv       # Usa vírgula como separador e mostra a 2ª coluna
cut -c1-5 texto.txt             # Mostra apenas os 5 primeiros caracteres
💬 Dica: o -d define o delimitador (por exemplo, vírgula ou ponto e vírgula).

🧾 5. head — Mostrar o Início do Arquivo
O head mostra as primeiras linhas de um arquivo.

📌 Sintaxe:
bash
Copiar código
head [opções] arquivo
💡 Exemplos:
bash
Copiar código
head arquivo.txt          # Mostra as 10 primeiras linhas
head -n 5 arquivo.txt     # Mostra as 5 primeiras linhas
💬 Dica: use head -n 20 para ver 20 linhas.

🔚 6. tail — Mostrar o Final do Arquivo
O tail mostra as últimas linhas de um arquivo.
É muito usado para monitorar logs em tempo real.

📌 Sintaxe:
bash
Copiar código
tail [opções] arquivo
💡 Exemplos:
bash
Copiar código
tail arquivo.txt           # Mostra as 10 últimas linhas
tail -n 20 arquivo.txt     # Mostra as últimas 20 linhas
tail -f log.txt            # Acompanha o arquivo em tempo real
💬 Dica: o -f é perfeito para ver logs sendo atualizados.

🧠 7. awk — Manipular e Processar Dados
O awk é uma ferramenta poderosa que permite ler colunas e aplicar condições.

📌 Sintaxe:
bash
Copiar código
awk 'condição {ação}' arquivo
💡 Exemplos:
bash
Copiar código
awk '{print $1}' nomes.txt               # Mostra a 1ª coluna
awk -F',' '{print $1, $3}' arquivo.csv   # Mostra a 1ª e 3ª coluna separadas por vírgula
awk '$3 > 50 {print $1, $3}' notas.txt   # Mostra quem tem nota maior que 50
💬 Dica: $1, $2, $3 representam colunas.

🧩 8. Combinando Comandos
Você pode juntar comandos usando o pipe (|).
O pipe envia a saída de um comando para a entrada do próximo.

💡 Exemplos:
bash
Copiar código
cat arquivo.txt | sort | uniq
grep "erro" log.txt | sort | uniq -c
cut -d',' -f2 dados.csv | sort | uniq -c
🔥 Isso é o poder do terminal: pequenos comandos combinados criam grandes resultados!

🧾 9. Salvando Resultados
Você pode salvar o resultado de qualquer comando em um novo arquivo usando > ou >>.

bash
Copiar código
sort dados.txt > dados_ordenados.txt     # Cria um novo arquivo
grep "OK" log.txt >> resultados.txt      # Adiciona ao final de outro arquivo
📊 10. Resumo Rápido
🧩 Comando	📖 Função	🧠 Exemplo
sort	Ordenar linhas	sort -n arquivo.txt
uniq	Remover duplicadas	uniq -c arquivo.txt
grep	Buscar padrões	grep "erro" log.txt
cut	Cortar colunas	cut -d',' -f1 arquivo.csv
head	Mostrar início	head -n 5 arquivo.txt
tail	Mostrar final	tail -f log.txt
awk	Manipular colunas	awk '{print $2}' arquivo.txt

✨ Conclusão
Agora você conhece os principais comandos de ordenação e filtragem no Linux!
Com eles, é possível analisar dados, processar logs e automatizar tarefas direto no terminal.
Esses comandos são a base para quem quer aprender Bash, Shell Script e DevOps.

👨‍💻 Autor
Marcos Luiz Mendes Junior
🎓 Estudante de Gestão da Tecnologia da Informação — PUC-RS
☁️ Apaixonado por Linux, Computação em Nuvem e Educação
🔗 GitHub • LinkedIn
