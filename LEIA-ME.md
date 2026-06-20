# Gerador de Painel — Indicadores de TI

Essa ferramenta transforma a planilha exportada do Tom Ticket direto no
painel atualizado, sem precisar me mandar o arquivo toda vez. Roda 100% no
seu navegador — a planilha não sai do seu computador, não precisa de
internet (depois de aberta) nem de instalar nada.

## 🆕 Botão "Sincronizar planilha" direto no painel

O painel (`index.html`) agora tem um botão **"Sincronizar planilha"** no
canto superior direito. Clicar nele abre esta ferramenta direto — você não
precisa guardar o link separado.

## 📁 O que tem aqui

```
index.html             → o painel em si (com o botão "Sincronizar planilha")
gerador_painel.html    → a ferramenta de sincronização
gerador.js             → lógica da ferramenta (não mexer)
xlsx.full.min.js       → biblioteca de leitura de Excel (não mexer)
```

**Importante:** suba os **4 arquivos juntos**, na **raiz** do repositório
(não dentro de pastas) — o botão "Sincronizar planilha" e o link "Voltar
ao painel" só funcionam se os arquivos estiverem lado a lado.

## 🚀 Como usar (toda vez que tiver uma planilha nova)

1. Abra o seu painel normalmente (o link do GitHub Pages)
2. Clique em **"Sincronizar planilha"** no canto superior direito — abre a ferramenta
3. Arraste a planilha exportada do Tom Ticket para a área pontilhada
   (ou clique nela para escolher o arquivo)
4. Clique em **"Gerar painel atualizado"**
5. Agora escolha uma das duas opções abaixo:

### Opção A — Baixar e subir manualmente (como antes)
Clique em **"Baixar index.html"** e suba no GitHub do jeito que você já faz.

### Opção B — Publicar direto, sem baixar nada (recomendado)
1. Clique em **"Publicar direto no GitHub (opcional)"** para abrir a seção
2. Na primeira vez, configure (só precisa fazer isso uma vez — fica salvo no navegador):
   - **Usuário/Organização**: `elielson60`
   - **Repositório**: o nome do seu repositório (ex: `indicador_tecnologia-KPIs`)
   - **Branch**: `main`
   - **Personal Access Token**: veja como criar abaixo
3. Clique em **"Publicar no GitHub"**
4. Em poucos segundos o painel já está atualizado no link do GitHub Pages

## 🔑 Como criar o Personal Access Token (só precisa fazer 1 vez)

1. Acesse: **github.com/settings/personal-access-tokens/new**
2. Em **"Repository access"**, escolha **"Only select repositories"** e selecione
   só o seu repositório do painel (nunca dê acesso a todos os repositórios)
3. Em **"Permissions" → "Repository permissions"**, encontre **"Contents"**
   e mude para **"Read and write"**
4. Role até o fim e clique em **"Generate token"**
5. Copie o token (começa com `github_pat_...`) e cole no campo da ferramenta

⚠️ **Esse token é como uma senha** — guarde com cuidado, nunca cole ele aqui
no chat comigo, e se desconfiar que vazou, revogue em
github.com/settings/personal-access-tokens.

O token fica salvo só dentro do seu navegador (na opção "Lembrar esses
dados neste navegador") — nunca é enviado para mim ou para qualquer
servidor além do próprio GitHub.

## 📤 Subir no GitHub (Opção A, se não usar o botão de publicar)

1. Acesse seu repositório (`indicadores-ti-kpi` ou o que você estiver usando)
2. Abra o arquivo `index.html` que já está lá
3. Clique no lápis (editar) → ou use **Add file → Upload files** arrastando
   o novo `index.html` por cima
4. **Commit changes**
5. Aguarde 1-2 minutos e abra o link do GitHub Pages com `Ctrl+Shift+R`
   (atualizar sem cache)

## ✅ O que a ferramenta faz sozinha

- Encontra a aba certa da planilha automaticamente (procura a coluna "Protocolo")
- Lê todos os chamados, calcula SLA, backlog, categorias, etc. — exatamente
  como eu fazia manualmente
- Também lê a aba "Pesquisa WIFI - Hotel" se ela existir na planilha nova
  — se não existir, mantém os dados de WiFi da última vez automaticamente
- Mostra um log na tela contando quantos chamados e quantos meses de WiFi
  encontrou, para você conferir que está tudo certo antes de baixar

## ⚠️ Se aparecer algum erro

Se a ferramenta não encontrar a coluna "Protocolo", ela avisa na tela — isso
geralmente significa que a planilha exportada tem um formato diferente do
esperado. Nesse caso, me manda a planilha aqui no chat que eu ajusto a
ferramenta para reconhecer o novo formato.
