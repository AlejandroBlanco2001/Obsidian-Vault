TTags #arquitectura-de-software #web #CSS 

Los colores dentro de nuestra pagina se pueden definir de 6 maneras:

- Hexadecimal `#ffffff`
	- Se expresa de la forma `#RRGGBB`
	- Que van desde 0-255
- RGB `rgb(255, 255, 255)`
	- Cada parametro indica la potencia de cada color
	- `rgb(red, green, blue)`
	- Los valores pueden ir de 0-255 o 0%-100%
- RGBA
	- Es lo mismo que RGB, sin embargo, el A indica la opacidad (Alfa)
	- `rgba(red, green, blue, alpha)`
- HSL
	- Este expresa otra escala de color que se usa 
	- `hsl(hue, saturation, lightness)`
	- Hue: Corresponde al valor de 0 a 360 grados en la circunferencia de color
		- 360 o 0 grados: Rojo
		- 120 grados: grados Verde
		- 240 grados: Azul
	- Saturation: Valor que va desde 0% a 100%, que representa la escala de color, siendo 0% escala de gris y 100% sin ninguna alteracion
	- Ligthness: Valor que corresponde a la luminosidad del color, 0% siendo negro y 100% siendo blanco
- HSLA
	- Es el mismo caso que el HSL, sin embargo, el A indica la opacidad (alfa)
	- `hsla(hue, saturation, ligthness, alpha)`
- Predefinidos
	- Son los valores por defecto que estipula el W3 para algunos colores y deben ser nombrados en ingles
	- Por ejemplo: red, yellow, blue

>[!NOTE]
>Escala de referencia de HSL
>![[Pasted image 20241007202402.png]]

