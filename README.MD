## Compilador de fontes customizadas para a lib PdfMake

### Instruções de build:

1 - Faça o download das fontes em formato `ttf` e coloque todas em um mesmo diretório

2 - É importante que o nome dos arquivos terminem com os sufixos `Regurlar`, `Italic`, `Bold` e `BoldItalic`. Por exemplo, se o nome da fonte é `Arial` antão devem ter os arquivos `Arial-Regular`, `Arial-Italic`, e assim por diante.

3 - Execute o arquivo index.js com o comando `node index.js`. O script perguntará qual o diretório contem os arquivos de fonte, informe no seguinte formato `./caminho/do/diretório`. Ao finalizar a execução do script será criado o arquivo `vfs_custom_fonts.js` na pasta raíz do projeto.

### Instruções de uso:

1 - Ao invés de importar o arquivo padrão de fontes do PdfMake, importe o arquivo customizado que foi gerado na etapa anterior como por exemplo: `import pdfFonts from './caminho/do/arquivo/vfs_custom_fonts';`

2 - Faça a configuração (De - Para) das fontes customizadas como no exeplo abaixo:

```javascript
pdfMake.vfs = pdfFonts.pdfMake.vfs;

pdfMake.fonts = {
  Inter: {
    normal: 'Inter-Regular.ttf',
    bold: 'Inter-Bold.ttf',
    italics: 'Inter-Italic.ttf',
    bolditalics: 'Inter-Bold.ttf',
  },
};
```

3 - Em seguida dentro do arquivo que contém a definição de corpo do documento PDF adicione a propriedade `defaultStyle` indicando o nome da fonte. Ex.:

```javascript
const document = {
  pageSize: 'A4',
  header: {},
  content: {},
  footer: {},
  styles: {},
  defaultStyle: {
    font: 'Inter',
  },
}
```
