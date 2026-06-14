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

1. Crie um repositório seguindo o [SDK.md](../core/docs/SDK.md)
2. Publique um GitHub Release com o zip do módulo
3. Abra um Pull Request adicionando sua entrada em `registry.json`
