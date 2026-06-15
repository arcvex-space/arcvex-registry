# Arcvex Registry

Catálogo público de módulos disponíveis no marketplace do Arcvex.

## Estrutura

```json
{
  "version": "1",
  "updatedAt": "YYYY-MM-DD",
  "modules": [
    {
      "id": "module-id",
      "name": "Nome do Módulo",
      "version": "1.0.0",
      "author": "autor",
      "description": "Descrição breve",
      "icon": "📦",
      "category": "categoria",
      "tags": ["tag1", "tag2"],
      "minCoreVersion": "0.3.0",
      "dependencies": [],
      "permissions": ["recurso:acao"],
      "download_url": "https://github.com/arcvex-space/module-id/releases/download/v1.0.0/module.zip"
    }
  ]
}
```

## Como publicar um módulo

A publicação é totalmente automatizada pelo `@arcvex/sdk`.

### 1. Instale o SDK

```bash
npm install -g @arcvex/sdk
```

### 2. Crie um token GitHub

Acesse **github.com → Settings → Developer settings → Personal access tokens → Tokens (classic)**, clique em **Generate new token (classic)**, marque o escopo `repo` e copie o valor gerado (`ghp_...`).

### 3. Configure o token

```bash
# Opção A — variável de ambiente (sessão atual)
export GITHUB_TOKEN=ghp_...

# Opção B — persistir entre sessões (adicione ao ~/.bashrc ou ~/.zshrc)
echo 'export GITHUB_TOKEN=ghp_...' >> ~/.zshrc && source ~/.zshrc

# Opção C — salvar em ~/.arcvex/config.json
echo '{ "githubToken": "ghp_..." }' > ~/.arcvex/config.json
```

### 4. Publique

```bash
cd seu-modulo/
arcvex module-publish
```

O comando cria a tag, aguarda o GitHub Actions gerar o ZIP, abre o PR automaticamente e o registry valida e faz o merge. O módulo aparece no marketplace em até 5 minutos.

> Para mais detalhes, consulte a documentação completa do SDK em [arcvex-space/arcvex-sdk](https://github.com/arcvex-space/arcvex-sdk).

## Validação automática

Todo PR passa por um workflow que verifica:
- Campos obrigatórios e formatos (`id`, `version`, `download_url`, etc.)
- Download e integridade do ZIP
- Consistência entre a entry do registry e o `module.json` dentro do ZIP

PRs que passam na validação são mergeados automaticamente. PRs que falham recebem um comentário com os erros específicos.
