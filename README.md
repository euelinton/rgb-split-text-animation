
# RGB Split Text Animation
> Efeito RGB utilizando a biblioteca Blotter Js

## Exemplo

A construção do efeito RGB é bem simples e pode ser resumida em 4 etapas:

1. Criação e estilização do texto 
```
const text = new Blotter.Text('PALAVRA', {
  family: 'serif', 
  size: 150, 
  fill: '#000'
})

```
    
2. Escolher o "material" e suas propriedades a serem utilizados no texto:

```

const material = new Blotter.ChannelSplitMaterial()

material.uniforms.uOffset.value = 0.05
material.uniforms.uRotation.value = 50
material.uniforms.uApplyBlur.value = 1
material.uniforms.uAnimateNoise.value = 0.3

```

3. Aplicar o efeito/material ao texto

```
const blotter = new Blotter(material, {
  texts: text
})

```

4. Adicionar o texto ao escopo da página

```

const scope = blotter.forText(text)
scope.appendTo(container)

```

Você pode ainda criar uma animação utilizando o cursor para alterar alguma das propriedades do efeito RGB:

```

document.onmousemove = e => {
  material.uniforms.uRotation.value = (e.clientX * .1)
  material.uniforms.uOffset.value = (e.clientX * 0.0001)
}

```
