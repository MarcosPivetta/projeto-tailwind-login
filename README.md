## projeto-tailwind-login

README do projeto com foco nas versões do Tailwind CSS presentes no repositório e instruções para rodar a aplicação localmente.

### Resumo rápido

- Arquivos principais:
	- `src/index.html` — página principal (front-end estático).
	- `src/style/style.css` — arquivo de entrada do Tailwind (onde ficam as diretivas @tailwind).
	- `src/style/output.css` — CSS gerado pelo CLI do Tailwind (gerado automaticamente pelo script `dev`).
- Versões detectadas (conforme `src/package.json`):
	- `tailwindcss`: ^4.1.16

> Observação: o `package.json` do projeto fica dentro da pasta `src/`. Todos os comandos npm abaixo devem ser executados a partir de `src/` (ou prefixados com `--prefix src`).

### Requisitos

- Node.js (recomendado) >= 16.x
- npm (vem com o Node.js)

### Como rodar localmente (modo desenvolvimento)

1. Abra um terminal e vá para a pasta `src` do projeto:

```bash
cd src
```

2. Instale as dependências:

```bash
npm install
```

3. Inicie o watcher do Tailwind (gera `style/output.css` e observa alterações):

```bash
npm run dev
```

Esse script usa o CLI do Tailwind para ler `./style/style.css` e gerar `./style/output.css` em modo watch. Enquanto estiver rodando, qualquer alteração em `style/style.css` (ou nos arquivos referenciados) vai atualizar `output.css` automaticamente.

4. Abra `src/index.html` no navegador. Para uma experiência mais real (evitar limitações do `file://`) recomenda-se abrir via servidor local. Exemplos rápidos:

Usando o `serve` via npx:

```bash
# no diretório src/
npx serve .
```

Ou usando o Live Server do VS Code (extensão) — basta abrir a pasta `src` no VS Code e iniciar o Live Server.

### Build para produção (minificar)

Se quiser gerar o CSS final minificado (sem watch), execute um comando similar a este dentro de `src/`:

```bash
npx @tailwindcss/cli -i ./style/style.css -o ./style/output.css --minify
```

Você também pode adicionar um script `build` em `src/package.json` para padronizar esse comando.

### Contrato rápido (entrada/saída)

- Entrada: arquivos fonte HTML e CSS em `src/` (principalmente `style/style.css`).
- Saída: CSS compilado em `src/style/output.css` pronto para uso pelo `index.html`.
- Erros comuns: `output.css` não atualizado (executar `npm run dev`), abrir `index.html` sem servidor (usar `npx serve` ou Live Server).

### Dicas e observações

- Se alterar os paths dos arquivos CSS no `package.json`, atualize também os caminhos usados no `index.html`.
- Para integrar deploy (ex.: subir apenas `output.css` e `index.html`), prefira gerar a versão minificada antes do deploy.
- Caso queira adicionar scripts de conveniência no `package.json` raiz, lembre-se de usar `--prefix src` ou mover o `package.json` para a raiz.


