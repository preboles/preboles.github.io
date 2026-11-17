# preboles.github.io
Repositorio de la app web Préboles

---

## Clasificación y creación de una guía de referencia para clasificación de imágenes

Información crítica puede ser obtenida basado en la osbservación y/o incorporación de registros audiovisuales. En un principio, constaba sólo de mi observación a través de diferentes ciudades, pero con el paso del tiempo, empecé a considerar la observación de cámaras en vivo que emiten a lo largo de Chile, y con eso sistematizar la recolección de información.

Proceso que ya desde su origen es ambiguo, dado que depende de mi punto de vista y consideración, si es que "ocurrió" el arrebol o no. Primero, entonces, hay que definir el arrebol. 


arrebol:
Definición: De arrebolar. Color rojo, especialmente el de las nubes iluminadas por los rayos del sol o el del rostro.

Estamos de acuerdo, entonces, que el arrebol proviene de la coloración de las nubes al amanecer o atardecer. 

La cual yo creo que es incompleta par definir el fenómeno por completo Creo que su componente temporal también es importante, así que debe ser tenida en cuenta. 

---

## Criterios de clasificación

Dado que el arrebol son ventanas en el día donde puede pasar dicho fenómeno, basta que el/la observador/a aviste **a lo menos una** coloración de nubes **suficiente**, con una intensidad dada, para considerar que hubo arrebol. 
Dicha la anterior premisa, es necesario considerar que el arrebol es un efecto bastante caótico, porque su aparición no solo depende de las condiciones metereológicas locales, sino que también de la geometría que poseen las nubes de camino a la dirección del sol. Por lo tanto, se considerarán los casos "simples" como una guía sobre cómo poder clasificar en tres escalas : 0,1,0.5

| Campo | Descripción |
|---|---|
| Definición de arrebol | El observador ve al menos una nube coloreada |
| Etiqueta | Valores posibles (por ejemplo: 1 = hubo arrebol, 0 = no hubo) |
| Evento | Amanecer o atardecer |

---
## Fuentes de información

En la pandemia aprendí a leer las nubes. Basta sólo tener tiempo e interés, la verdad. Cualquiera puede hacerlo. Ayuda, sin embargo, estar en un lugar donde el clima sea, digamos, propicio para la ocurrencia de tal fenómeno físico, esa es la verdadera suerte. Ahí entonces estaba yo entonces, en Valparaíso, encerrado por la pandemia. Bastó un par de días para notar patrones en las nubes, bastaron un par de meses para que las primeras predicciones empezaran a cumplirse. 
Y como varias personas observadores, jugamos a predecir el futuro en base a la experiencia: Las nubes tienen diferentes alturas, son diferentes estados del mismo gas, se mueven a diferentes velocidades, reflejan o dispersan la luz de forma diferente. Estos conocimientos naturales fueron utilizados para sacar a pasear a los perritos, ir a comprar pan, salir a tomar chela a la playa, o hacer fotografías. 

Por cosas de la vida, me tocaba viajar por diferentes ciudades de Chile e iba registrando las fechas de las tardes en las que me encontraba con un arrebol. Cuando el concepto del **Modelo Local** apareció, fue preguntándome cuál sería la ciudad con más arreboles de Chile. 

Ahí fue cuando supe la existencia de Open Meteo: hasta el 2025, sin duda sabía la existencia de grandes bases de datos metereológicos, pero no había ninguna configuración mental personal que requiriera de aquellos datos, ahora sí existía: Si yo podía predecir, cláramente podría diseñar un sistema básico para que lo hiciera por mi, sin tener que estar en el lugar para hacer una predicción. 

Con la primera versión de préboles, que ahora yo llamo el **modelo local** considebara que el arrebol sólo dependía de las nubes que estaban diréctamente por sobre nuestras cabezas, las cuales, dada la grílla de Open-Meteo, era una superficie alrededor de 100 km al cuadrado (11x11 km). Para mi, esto era suficiente. 

Con los meses, fui monitoreando las predicciones en varias partes de Chile y con sorpresa veía que, muchas veces que yo decía que no habría (y el detector si) ocurría el arrebol. Como también, muchas veces terminaba mirando puestas de sol espectaculares, mientras el detector decía que la probabiliadad de ocurrencia tenía al 0%. Algo faltaba aún.

Como faltaba información, me puse a recolectar posibles fuentes de datos. Ya no bastaba la expeciencia: era muy lenta (con suerte 2 mediciones por día) y dependia de la observación y amabilidad de otras personas para obtener tales observaciones. Así fue como di con una serie de cámaras que emiten en directo en diferentes puntos de chile. De norte a sur: Mejillones, Observatorio ALMA, Vallenar, La Serena, Valparaíso, Santiago, San Fernando, Concepción, Puerto Williams, Punta Arenas. Estas serán las que se llamarán las "Cámaras en vivo", y serán la gran fuente de información de este proyecto. Por otro lado, también es posible consultar las cámaras de los diferente aerodromos en Chile, los cuales van publicando fotos en intervalos regulares de una hora. Por lo tanto, estas cámaras se usan más para "confirmar" que hubo un arrebol, más que para "desconfirmar" (es decir, es mucho más probable clasificar un atardecer con un 1, que con un 0). Esto puede introducir sesgos. 

Dicho lo anterior, las fuentes de información de Préboles son:

1. Observación directa: Basada en la expertiz de la persona que reporta. También se considera en este grupo la obtención de una fotografía o archivos similares.
2. Emisiones en vivo de cámaras públivas (digamos): Diversas personas mantienen emisiones en vivo de lo que sucede en diferentes puntos del país. Se ha escrito y diseñado un sistema basado en bash script que graba, recolecta y analiza estas transmisiones.
3. Cámaras de Aeródromos: Al parecer, por normas aeronáuticas, en este tipo de lugares es necesario tener imágenes en vivo cada cierto tiempo, lo que lo hace una excelente fuente de información a lo largo de chile.   

Lamentáblemente no todo es bueno. Este sistema presenta debilidades estadísticas: los sesgos. Al ser el arrebol un fenómeno temporal, presenta por definición, variabilidad. Esto induce sesgos en los datos que son reportados. En principio, los sesgos tendrían que auto regularse al verse incrementada la muestra, pero es necesario tener en cuenta esto en las primeras etapas de este desarrollo. Es por esto que he creado la categoría de 0.5, dado que no estoy seguro si ocurrió o no. 

Asi que con esto es posible clasificar el arrebol, en OCURRE, NO OCURRE; MÄS O MENOS NOMAS. 

Lo que sigue, son ejemplos donde YO CLASIFICO el arrebol en base a lo que yo considero la fenomenología asociada al arrebol. Sería interesante que alguien clasificara de otra forma, dadas las mismas reglas.

---

### `ObservacionDirecta/`

<table>
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/05_1.JPG" width="220"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0742.JPG" width="220"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_1777.JPG" width="220"><br>
      <sub>Sí</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/20201005_195049.jpg" width="220"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_4472.JPG" width="220"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_5091.JPG" width="220"><br>
      <sub>Más o menos</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0327.JPG" width="220"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0519.JPG" width="220"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0625.JPG" width="220"><br>
      <sub>No</sub>
    </td>
  </tr>
</table>

> **Nota:** Cuatro de las seis imágenes son capturas del 2026-11-12. 

---

### `CamarasEnVivo/`

<table>
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Captura%20de%20pantalla%20de%202026-11-16%2007-36-36.png" width="220"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0742.JPG" width="220"><br>
      <sub>Sí</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src=https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Captura de pantalla de 2026-11-16 07-34-59.png" width="220"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_4472.JPG" width="220"><br>
      <sub>Más o menos</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0327.JPG" width="220"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_0519.JPG" width="220"><br>
      <sub>No</sub>
    </td>
  </tr>
</table>


| Archivo | Origen del nombre | Fecha (si se deduce del nombre) | Formato |
|---|---|---|---|
| `05_1.JPG` | Nombre manual | — | JPG |
| `20201005_195049.jpg` | Marca de tiempo | 2020-10-05, 19:50:49 | jpg |
| `IMG_0327.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_0519.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_0625.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_0742.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_1777.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_20200829_231205_711.jpg` | Cámara de teléfono (marca de tiempo) | 2020-08-29, 23:12:05 (hora según el nombre) | jpg |
| `IMG_4472.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_5091.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_7448.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_8352.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_8499.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_8879.JPG` | Cámara (numeración correlativa) | — | JPG |
| `IMG_8968.JPG` | Cámara (numeración correlativa) | — | JPG |


---

## Resumen

