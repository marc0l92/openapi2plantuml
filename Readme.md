# OpenApi 2 Plantuml

![Known Vulnerabilities](https://snyk.io/test/github/marc0l92/openapi2plantuml/badge.svg)

Parse your REST API documentation written using OpenApi or Swagger to generate PlantUML diagrams.

[See this library in action](https://marc0l92.github.io/openapi2plantuml/test/index.html)

## Installation

```bash
npm install openapi2plantuml
```

## Usage

```javascript
const OpenApi2PlantUml = require('openapi2plantuml');

const documentation = `
openapi: 3.0.0
info:
  title: My amazing API
  version: 1.0.0
[...]
`

const generator = new OpenApi2PlantUml(documentation)
await generator.execute()
const diagrams = generator.getDiagrams()
```

An example of `getDiagrams()` output is the following:
```json
{
  "/this/is/a/path": {
      "POST": {
        "request": {
          "diagram": "The plantUml diagram in text format",
          "imageUri": "The URI of the image that renders the diagram"
        },
        "response": {
          "diagram": "The plantUml diagram in text format",
          "imageUri": "The URI of the image that renders the diagram"
        }
      }
    }
}
```

## Options

The constructor accepts as second argument a options object.
```javascript
const generator = new OpenApi2PlantUml(documentation, {
  serverUrl: 'https://www.plantuml.com/plantuml',
  format: 'svg',
  diagramHeader: '',
  colors: true,
})
```

| Name | Type | Default | Description |
| ---- | ---- | ------- | ----------- |
| `serverUrl` | `string` | `'https://www.plantuml.com/plantuml'` | The URL of the PlantUML server. |
| `format` | `string` | `'png'` | The format of the image generated (png or svg). |
| `diagramHeader` | `string` | `''` | The header of the diagram that will be put at the begin of each diagram. This option is usally used to apply a default theme to all diagrams. |
| `colors` | `boolean` | `true` | Enable colors to class properties and types. |
