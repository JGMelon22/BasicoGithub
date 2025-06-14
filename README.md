# Site 
# https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

1 --> ssh-keygen -t ed25519 -C "your_email@example.com"
2 --> eval "$(ssh-agent -s)"
3 --> ssh-add ~/.ssh/id_ed25519

# Site 2
# https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
1 --> cat ~/.ssh/id_ed25519.pub

# Comandos adicionar usuário e email ao git bash
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"

# Site para o gitignore 
https://github.com/github/gitignore

# O que fazer do git push inicial? 
1 --> git init
2 --> vim .gitignore
    2.1 --> Ctrl + Shift + V 
    2.2 --> Aperte ":", digite "wq!" e aperte enter
3 --> git add .
4 --> git commit -m "first commit"
5 --> git branch -M main
6 --> git remote add origin git@github.com:JGMelon22/TesteRepo2.git
7 --> git push -u origin main

# O que fazer nos commits seguintes?
1 --> git add .
2 --> git commit -m "Sua mensagem descritiva"
3 --> git push
