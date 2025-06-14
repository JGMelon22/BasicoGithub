# Guia Completo: Git e SSH - Configuração e Uso

## 📋 Índice
- [Gerando Chave SSH](#gerando-chave-ssh)
- [Conectando com o GitHub via SSH](#conectando-com-o-github-via-ssh)
- [Configuração Global do Git](#configuração-global-do-git)
- [Primeiro Push de um Repositório](#primeiro-push-de-um-repositório)
- [Commits Subsequentes](#commits-subsequentes)
- [Recursos Adicionais](#recursos-adicionais)

---

## 🔐 Gerando Chave SSH

Para estabelecer uma conexão segura com o GitHub, você precisa gerar uma chave SSH. Este processo cria um par de chaves (pública e privada) para autenticação.

### Passos:

1. **Gerar a chave SSH**
   ```bash
   ssh-keygen -t ed25519 -C "seu_email@exemplo.com"
   ```
   > **Nota:** Substitua `seu_email@exemplo.com` pelo seu email do GitHub

2. **Iniciar o agente SSH**
   ```bash
   eval "$(ssh-agent -s)"
   ```

3. **Adicionar a chave ao agente SSH**
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

**Referência oficial:** [GitHub Docs - Generating SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

---

## 🔗 Conectando com o GitHub via SSH

Após gerar a chave SSH, você precisa adicioná-la à sua conta do GitHub.

### Como obter sua chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

### Próximos passos:
1. Copie a saída completa do comando acima
2. Acesse o GitHub → Settings → SSH and GPG keys
3. Clique em "New SSH key"
4. Cole sua chave pública no campo "Key"
5. Adicione um título descritivo

**Referência oficial:** [GitHub Docs - Adding SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

---

## 👤 Configuração Global do Git

Configure suas informações de usuário globalmente para todos os repositórios:

```bash
git config --global user.name "SEU NOME COMPLETO"
git config --global user.email "seu_email@exemplo.com"
```

> **Dica:** Use o mesmo email configurado na sua conta do GitHub para melhor integração.

---

## 🚀 Primeiro Push de um Repositório

Para repositórios novos, siga esta sequência de comandos:

### Passo a passo:

1. **Inicializar repositório Git**
   ```bash
   git init
   ```

2. **Criar arquivo .gitignore**
   ```bash
   vim .gitignore
   ```
   - **No editor Vim:**
     - Cole o conteúdo do .gitignore: `Ctrl + Shift + V`
     - Para salvar e sair: digite `:wq!` e pressione `Enter`

3. **Adicionar arquivos ao staging**
   ```bash
   git add .
   ```

4. **Fazer o primeiro commit**
   ```bash
   git commit -m "Initial commit"
   ```

5. **Renomear branch para main**
   ```bash
   git branch -M main
   ```

6. **Conectar com repositório remoto**
   ```bash
   git remote add origin git@github.com:SEU_USUARIO/SEU_REPOSITORIO.git
   ```
   > **Importante:** Substitua `SEU_USUARIO` e `SEU_REPOSITORIO` pelos valores corretos

7. **Fazer push inicial**
   ```bash
   git push -u origin main
   ```

---

## 🔄 Commits Subsequentes

Para mudanças futuras no projeto, use este fluxo simplificado:

```bash
# Adicionar mudanças
git add .

# Fazer commit com mensagem descritiva
git commit -m "Sua mensagem descritiva aqui"

# Enviar para o repositório remoto
git push
```

### 💡 Boas práticas para mensagens de commit:
- Use mensagens claras e descritivas
- Comece com verbo no imperativo (ex: "Add", "Fix", "Update")
- Seja específico sobre o que foi alterado

---

## 📚 Recursos Adicionais

### Templates de .gitignore
Para diferentes tipos de projeto, acesse a coleção oficial do GitHub:
**[GitHub .gitignore Templates](https://github.com/github/gitignore)**

### Comandos Git úteis:
```bash
# Ver status dos arquivos
git status

# Ver histórico de commits
git log --oneline

# Ver diferenças não commitadas
git diff

# Desfazer último commit (mantendo mudanças)
git reset --soft HEAD~1
```
