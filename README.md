# painel-portfolio

Casca estática do painel de portfólio pessoal. **Este repositório não contém dado
nenhum** — é só HTML e JavaScript de login.

## Como funciona

```
notas do vault (privado)  →  publicar_painel.py  →  Supabase (RLS)  →  esta página
```

A página abre num formulário de email. O Supabase manda um magic link; a sessão
autenticada busca as iniciativas, filtradas por Row Level Security ao `user_id`
do dono. Sem sessão válida, a página é um formulário vazio — e é isso que qualquer
pessoa que achar a URL vai ver.

A chave embutida no HTML é a **publishable key**, desenhada para viver no cliente.
Ela não dá acesso a nada por si só: toda leitura passa pela RLS.

## Gerado, não editado à mão

`index.html` é gerado por `03-recursos/tools/publicar_painel.py --casca` no vault
Aruk (privado). Editar aqui direto é perder a mudança na próxima geração.
