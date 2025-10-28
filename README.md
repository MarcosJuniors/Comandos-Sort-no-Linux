# Comandos-Sort-no-Linux
Este repositório contém uma documentação prática sobre o comando sort no Linux, utilizado para ordenação e filtragem de dados em arquivos de texto. São abordadas suas principais opções, exemplos de uso e dicas para aplicar ordenações alfabéticas, numéricas e personalizadas em diferentes contextos.

#!/bin/bash
# ==============================================
# 🐧 ORDENADOR DE ARQUIVOS — Comando sort no Linux
# Autor: Marcos Luiz Mendes Junior

# 🧊 Banner
echo "=============================================="
echo "     🐧 ORDENADOR DE ARQUIVOS - Linux Sort 🧊   "
echo "=============================================="

# Solicita o nome do arquivo
read -p "Digite o nome do arquivo a ser ordenado: " arquivo

# Verifica se o arquivo existe
if [ -f "$arquivo" ]; then
    echo "Escolha uma opção de ordenação:"
    echo "1 - Ordem alfabética (A-Z)"
    echo "2 - Ordem alfabética invertida (Z-A)"
    echo "3 - Ordem numérica"
    echo "4 - Ordem numérica invertida"
    echo "5 - Remover duplicatas e ordenar"
    read -p "Digite o número da opção: " opcao

    case $opcao in
        1) sort "$arquivo" -o "ordenado_$arquivo" ;;
        2) sort -r "$arquivo" -o "ordenado_$arquivo" ;;
        3) sort -n "$arquivo" -o "ordenado_$arquivo" ;;
        4) sort -n -r "$arquivo" -o "ordenado_$arquivo" ;;
        5) sort -u "$arquivo" -o "ordenado_$arquivo" ;;
        *) echo "❌ Opção inválida!"; exit 1 ;;
    esac

    echo "✅ Arquivo ordenado com sucesso!"
    echo "📁 Resultado salvo em: ordenado_$arquivo"
else
    echo "❌ Arquivo não encontrado! Verifique o nome e tente novamente."
fi

🧾 Saiba mais

📚 Documentação oficial:
👉 GNU Sort Manual

📖 Ajuda no terminal:

man sort

🐧 Licença

Distribuído livremente sob a licença MIT
.
Feito com ❤️ por Marcos Luiz Mendes Junior — apaixonado por Linux, Cloud e Dados ☁️💻

“Automatizar é libertar o tempo para pensar melhor.” – 🐧


---

✅ **Instruções para subir no GitHub:**
```bash
# Crie a pasta do projeto
mkdir linux-sort && cd linux-sort

# Crie os arquivos
nano README.md
# cole o conteúdo acima do README

nano ordenar.sh
# cole o conteúdo do script

# Torne o script executável
chmod +x ordenar.sh

# Inicie o repositório e publique
git init
git add .
git commit -m "Guia completo do comando sort 🐧"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/linux-sort.git
git push -u origin main
