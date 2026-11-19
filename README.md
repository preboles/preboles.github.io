# preboles.github.io
Repositorio de la app web Préboles

---
## Clasificación y creación de una guía de referencia para clasificación de imágenes del arrebol

En la pandemia del 2020 aprendí a leer las nubes. Basta con tener tiempo e interés, la verdad. Cualquiera puede hacerlo. Y en ese episodio, tuve tiempo de sobra para mirar el cielo, y no tan lejos esta vez. Ayuda, sin embargo, estar en un lugar donde el clima sea propicio para la ocurrencia de este fenómeno físico: esa es la verdadera suerte. Ahí estaba yo entonces, en Valparaíso, encerrado por la pandemia. Luego de generar un interés geniuno, bastó un part de diás para notar patrones en las nubes, y bastaron un par de meses para que las primeras predicciones empezaran a cumplirse de forma esporádica. 

Como varios observadores, jugábamos a predecir el futuro en base a la experiencia: las nubes tienen diferentes alturas, son diferentes estados del mismo gas, se mueven a diferentes velocidades, reflejan o dispersan la luz de forma diferente. Estos conocimientos naturales fueron utilizados, en ese entonces, para salir pasear, hacer fotografías o a tomar chela a la playa (eran mis preocupaciones)

La palabra arrebol proviene del latín rubor ("enrojecimiento" o "rojez") o rubeus ("rojizo"), a través de formas relacionadas con el enrojecimiento. La RAE lo define de la siguiente forma:

> Arrebol: De arrebolar. Color rojo, especialmente el de las nubes iluminadas por los rayos del sol o el del rostro.

Aún así, yo creo que esta definicion es insuficiente o incompleta para poder hablar o describir el conjunto de fenómenos físicos que ocurren en el Arrebol. Es necesario observar y recolectar información de forma sistemática para su real caracterización cuando el arrebol ocurre. 

En un principio, constaba sólo de mi observación a través de diferentes ciudades. Por cosas de la vida, me tocaba viajar por diferentes ciudades de Chile e iba registrando las fechas de las tardes en las que me encontraba con un arrebol. Con el paso del tiempo, empecé a considerar la observación de cámaras en vivo que emiten a lo largo de Chile, y con eso sistematizar la recolección de información.

Cuando apareció el concepto de **Modelo de predicción Local**, fue preguntándome cuál sería la ciudad con más arreboles de Chile. La incorporación de registros audiovisuales pueden aportar información crítica, y su automatización, en estos tiempo, no es sólo posible, sino que necesaria.

---

## Criterios de clasificación

Dado que el arrebol son ventanas en el día donde puede pasar dicho fenómeno, basta que el/la observador/a aviste **a lo menos una** coloración de nubes **suficiente**, con una intensidad dada, para considerar que hubo arrebol. 
Dicha la anterior premisa, es necesario considerar que el arrebol es un **fenómeno caótico**, porque su aparición no solo depende de las condiciones metereológicas locales, sino que también de la geometría que poseen las nubes de camino a la dirección del sol. Por lo tanto, se considerarán los casos "simples" como una guía sobre cómo poder clasificar el fenómeno. Las escalas son las siguientes:

| Etiqueta | Significado | Criterio de clasificación |
|---|---|---|
| **1** | Sí hubo arrebol | El observador avista al menos una nube con coloración suficiente e intensidad clara, en la ventana del amanecer o atardecer |
| **0.5** | Más o menos / dudoso | Hay indicios de coloración, pero no se está seguro de si constituye arrebol |
| **0** | No hubo arrebol | No se observa coloración suficiente en las nubes durante la ventana correspondiente |

---

## Fuentes de información

Open-Meteo es, por excelencia, la fuente principal de datos metereológicos, que se pueden consultar de forma gratuita. Hasta el 2025, sin duda sabía la existencia de grandes bases de datos metereológicos, pero no había ninguna configuración mental personal que requiriera de aquellos datos. En ese momento, me di cuenta que si yo pude desarrollar un método para predecir con cierto éxito, cláramente podría diseñar un sistema básico para que lo hiciera por mi, sin tener que estar en el lugar para hacer una predicción. 

Con la primera versión de préboles, que ahora yo llamo el **modelo local** considebara que el arrebol sólo dependía de las nubes que estaban diréctamente por sobre nuestras cabezas, las cuales, dada la grílla de Open-Meteo, era una superficie alrededor de 100 km al cuadrado (11x11 km). Para mi, esto era suficiente. 

Con los meses, fui monitoreando las predicciones en varias partes de Chile y con sorpresa veía que, muchas veces que yo decía que no habría (y el detector si) ocurría el arrebol. Como también, muchas veces terminaba mirando puestas de sol espectaculares, mientras el detector decía que la probabiliadad de ocurrencia tenía al 0%. Algo faltaba aún.

Como faltaba información, me puse a recolectar posibles fuentes de datos. Ya no bastaba la expeciencia: era muy lenta (con suerte 2 mediciones por día) y dependia de la observación y amabilidad de otras personas para obtener tales observaciones. Así fue como di con una serie de cámaras que emiten en directo en diferentes puntos de chile. De norte a sur: Mejillones, Observatorio ALMA, Vallenar, La Serena, Valparaíso, Santiago, San Fernando, Concepción, Puerto Williams, Punta Arenas. Estas serán las que se llamarán las "Cámaras en vivo", y serán la gran fuente de información de este proyecto. Por otro lado, también es posible consultar las cámaras de los diferente aerodromos en Chile, los cuales van publicando fotos en intervalos regulares de una hora. Por lo tanto, estas cámaras se usan más para "confirmar" que hubo un arrebol, más que para "desconfirmar" (es decir, es mucho más probable clasificar un atardecer con un 1, que con un 0). Esto puede introducir sesgos. 

IMAGEN DE CHILE CON LAS LOCALIZACION DE LAS CAMARAS

Dicho lo anterior, las fuentes de información de Préboles son:

1. **Observación directa**: Basada en la expertiz de la persona que reporta. También se considera en este grupo la obtención de una fotografía o archivos similares.
2. **Emisiones en vivo de cámaras públicas** (digamos): Diversas personas mantienen emisiones en vivo de lo que sucede en diferentes puntos del país. Se ha escrito y diseñado un sistema basado en bash script que graba, recolecta y analiza estas transmisiones.
3. **Cámaras de Aeródromos**: Al parecer, por normas aeronáuticas, en este tipo de lugares es necesario tener imágenes en vivo cada cierto tiempo, lo que lo hace una excelente fuente de información a lo largo de chile.   

Lamentáblemente no todo es bueno. Este sistema presenta debilidades estadísticas: los sesgos. Al ser el arrebol un fenómeno temporal, presenta por definición, variabilidad. Esto induce sesgos en los datos que son reportados. En principio, los sesgos tendrían que auto regularse al verse incrementada la muestra, pero es necesario tener en cuenta esto en las primeras etapas de este desarrollo. Es por esto que he creado la categoría de 0.5, dado que no estoy seguro si ocurrió o no. 

---

### `ObservacionDirecta/`

Lo que sigue, son ejemplos donde YO CLASIFICO el arrebol en base a lo que yo considero la fenomenología asociada al arrebol. Sería interesante que alguien clasificara de otra forma, dadas las mismas reglas.

<table>
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/LasCampanas_SI.jpg" width="220"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_5091.JPG" width="220"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_1777.JPG" width="220"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_20200829_231205_711.jpg" width="220"><br>
      <sub>Sí</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/05_1.JPG" width="220"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_4472.JPG" width="220"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_8879.JPG" width="220"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/20201005_195049.jpg" width="220"><br>
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
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_1393_NO.JPG" width="220"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/ObservacionDirecta/IMG_1509_No.JPG" width="220"><br>
      <sub>No</sub>
    </td>
  </tr>
</table>

> **Nota:** . 

---

### `CamarasEnVivo/`

<table>
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Valparaiso_si.jpg" width="320"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Pichilemu_28_07_2026.jpg" width="320"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Captura%20de%20pantalla%20de%202026-11-16%2007-36-36.png" width="320"><br>
      <sub>Sí</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Captura%20de%20pantalla%20de%202026-11-16%2007-34-59.png" width="320"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Quintero_masomenos.jpg" width="320"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/SanAntonioNo.jpg" width="320"><br>
      <sub>Más o menos</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Concepcion_28_09_2026_NO.jpg" width="320"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/Mejillones_21_09_2026_NO.jpg" width="320"><br>
      <sub>No</sub>
    </td>
        <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasEnVivo/ALMA_28_09_2026_NO.jpg" width="320"><br>
      <sub>No</sub>
    </td>
  </tr>
</table>

---

### `CamarasDeAerodromos/`

<table>
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/APEX_si.jpg" width="320"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/Dalcahue_SI.jpg" width="320"><br>
      <sub>Sí</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/Si.jpg" width="320"><br>
      <sub>Sí</sub>
    </td>
  </tr>

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/Palena_masomenos.jpg" width="320"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/masomens.jpg" width="320"><br>
      <sub>Más o menos</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/Rodelillos_masomenos.jpg" width="320"><br>
      <sub>Más o menos</sub>
    </td>
  </tr>
  

  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/SantoDomingo_no.jpg" width="320"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/LaFlorida_no.jpg" width="320"><br>
      <sub>No</sub>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/CamarasDeAeropuertos/AerodromoBalmaceda_niIdea.jpg" width="320"><br>
      <sub>No (?) </sub>
    </td>
  </tr>
</table>




---

## Resumen

