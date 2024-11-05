Tags #arquitectura-de-software #CSS #web 

CSS es el acronimo de Cascade Style Sheets, es una forma de especificar los estilos dentro de nuestra pagina web.

Siempre podemos hacerlo de dos maneras:
- CSS externo mediante el uso de la tag <link>
- CSS en linea

CSS se compone de reglas de la siguiente manera

```css
/*

Selector {
  atributo: valor
}

*/

h1 { 
  color: blue
}
```

Para el tipo de selectores se usa las siguientes opciones:
- Tipo
- Clase
- Identificador
- Atributos

## Selector de tipo

Los selectores de tipo hacen referencia al tipo de etiqueta, basicamente, a que etiqueta HTML queremos afectar. Esto es un selector global

```css
h1 { 
  color: blue
}

p {
  color: red
}
```

## Selector de clase

Los selectores de tipo clase nos permiten realizar un cambio de manera mas selectiva a un grupo de etiquetas que comparten una clase. Se usa el simbolo `.cards`

```css
.cards {
  color: yellow;
}
```

## Selector de ID

Los selectores de tipo ID nos permiten realizar un cambio de manera completamente unica y particular, donde solo queremos afectar a un unico elemento. Se usa el simbolo `#id`

```css
#card {
  color: green;
}
```

## Selector de atributo

Los selectores de tipo atributo nos permite realizar un cambio de manera mas selectiva, donde afectamos a ciertas etiquetas que tengan un atributo en particular.

```css
a[href="some_domain"]{
  color: grey;
}
```

