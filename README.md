# preboles.github.io

Préboles: Predictor de arreboles

<img src="https://raw.githubusercontent.com/nicomedinap/nicomedinap.github.io/refs/heads/master/imagenes/preboles.png" alt="Description" width="330" height="200" >
---
En la pandemia del 2020 aprendí a leer las nubes. Basta con tener tiempo e interés, la verdad. Cualquiera puede hacerlo. Y en ese episodio, tuve tiempo de sobra para mirar el cielo, y no tan lejos esta vez. Ayuda, sin embargo, estar en un lugar donde el clima sea propicio para la ocurrencia de este fenómeno físico: esa es la verdadera suerte. Ahí estaba yo entonces, en Valparaíso, encerrado por la pandemia. Luego de generar un interés geniuno, bastó un par de diás para notar patrones en las nubes, y bastaron un par de meses para que las primeras predicciones empezaran a cumplirse de forma esporádica. 

Como varios observadores, jugábamos a predecir el futuro en base a la experiencia: las nubes tienen diferentes alturas, son diferentes estados del mismo gas, se mueven a diferentes velocidades, reflejan o dispersan la luz de forma diferente. Estos conocimientos naturales fueron utilizados, en ese entonces, para salir pasear, hacer fotografías o a tomar chela en los roqueríos de la playa, las cuales eran mi procupaciones del momento.

---


La palabra arrebol proviene del latín rubor ("enrojecimiento" o "rojez") o rubeus ("rojizo"), a través de formas relacionadas con el enrojecimiento. La RAE lo define de la siguiente forma:

> Arrebol: De arrebolar. Color rojo, especialmente el de las nubes iluminadas por los rayos del sol o el del rostro.

Aún así, yo creo que esta definicion es insuficiente o incompleta para poder hablar o describir el conjunto de fenómenos físicos que ocurren en el Arrebol. Es necesario observar y recolectar información de forma sistemática para su real caracterización cuando el arrebol ocurre. 

El modelo óptico de Préboles intenta estimar qué tan favorables son las condiciones para observar un arrebol al amanecer o al atardecer. La diferencia con mi primer modelo, al que llamo el modelo **local** $P_{\rm local}$, es que ya no evalúo únicamente la nubosidad del lugar donde está el observador. Ahora intento representar la ruta de la luz:

$$ \text{Sol}\longrightarrow\text{atmósfera}\longrightarrow \text{nube}\longrightarrow\text{atmósfera}\longrightarrow\text{observador} $$

Según las aproximaciones del modelo, una nube contribuye al resultado si:

1. existe nubosidad en su posición y altura;
2. recibe iluminación solar;
3. la geometría Sol–nube–observador favorece la interacción óptica adoptada;
4. la luz puede llegar a la nube y salir de ella sin una atenuación excesiva;
5. el terreno y las nubes interpuestas no bloquean el trayecto;
6. su contribución es significativa para alguno de los ángulos de visión evaluados.

El resultado se construye sumando las contribuciones de las celdas nubosas a lo largo de rayos de observación, para una elevación solar dada. A ese estadístico lo llamo el **modelo óptico** $P_{\rm óptico}$, y existe uno para cada valor de elevación solar $\alpha_i$.

Pero un arrebol no es un instante, es una ventana. Por eso al final opero sobre todo el intervalo: sumo las intensidades $\Delta I$ de los rayos para cada elevación solar $\alpha_i$ y construyo un estadístico que indique si se dieron las condiciones físicas para que ocurriera el arrebol (un 1) o no se dieron, o no ocurrió (un 0). Ese número lo llamo el **índice** $Q(\alpha)$, por ninguna razón particular: la $Q$ viene después de la $P$.



---

## Fuentes de información

En un principio, constaba sólo de mi observación a través de diferentes ciudades. Por cosas de la vida, me tocaba viajar por diferentes ciudades de Chile e iba registrando las fechas de las tardes en las que me encontraba con un arrebol. Con el paso del tiempo, empecé a considerar la observación de cámaras en vivo que emiten a lo largo de Chile, y con eso sistematizar la recolección de información.

Cuando apareció el concepto de **Modelo de predicción Local**, fue preguntándome cuál sería la ciudad con más arreboles de Chile. La incorporación de registros audiovisuales pueden aportar información crítica, y su automatización, en estos tiempo, no es sólo posible, sino que necesaria. Cuando el modelo óptico 

Open-Meteo es, por excelencia, la fuente principal de datos metereológicos, que se pueden consultar de forma gratuita. Hasta el 2025, sin duda sabía la existencia de grandes bases de datos metereológicos, pero no había ninguna configuración mental personal que requiriera de aquellos datos. En ese momento, me di cuenta que si yo pude desarrollar un método para predecir con cierto éxito, cláramente podría diseñar un sistema básico para que lo hiciera por mi, sin tener que estar en el lugar para hacer una predicción. 

Con la primera versión de préboles, que ahora yo llamo el **modelo local** considebara que el arrebol sólo dependía de las nubes que estaban diréctamente por sobre nuestras cabezas, las cuales, dada la grílla de Open-Meteo, era una superficie alrededor de 100 km al cuadrado (11x11 km). Para mi, esto era suficiente. 

Con los meses, fui monitoreando las predicciones en varias partes de Chile y con sorpresa veía que, muchas veces que yo decía que no habría (y el detector si) ocurría el arrebol. Como también, muchas veces terminaba mirando puestas de sol espectaculares, mientras el detector decía que la probabiliadad de ocurrencia tenía al 0%. Algo faltaba aún.

Como faltaba información, me puse a recolectar posibles fuentes de datos. Ya no bastaba la expeciencia: era muy lenta (con suerte 2 mediciones por día) y dependia de la observación y amabilidad de otras personas para obtener tales observaciones. Así fue como di con una serie de cámaras que emiten en directo en diferentes puntos de chile. De norte a sur: Mejillones, Observatorio ALMA, Vallenar, La Serena, Valparaíso, Santiago, San Fernando, Concepción, Puerto Williams, Punta Arenas. Estas serán las que se llamarán las "Cámaras en vivo", y serán la gran fuente de información de este proyecto. Por otro lado, también es posible consultar las cámaras de los diferente aerodromos en Chile, los cuales van publicando fotos en intervalos regulares de una hora. Por lo tanto, estas cámaras se usan más para "confirmar" que hubo un arrebol, más que para "desconfirmar" (es decir, es mucho más probable clasificar un atardecer con un 1, que con un 0). Esto puede introducir sesgos. 

IMAGEN DE CHILE CON LAS LOCALIZACION DE LAS CAMARAS

<img src="https://raw.githubusercontent.com/nicomedinap/preboles.github.io/refs/heads/main/Documentacion/Clasificacion/chile_camaras_aerodromos.jpg" alt="Mapa de cámaras en Chile" width="220">

Dicho lo anterior, las fuentes de información de Préboles son:

1. **Observación directa**: Basada en la expertiz de la persona que reporta. También se considera en este grupo la obtención de una fotografía o archivos similares.
2. **Emisiones en vivo de cámaras públicas** (digamos): Diversas personas mantienen emisiones en vivo de lo que sucede en diferentes puntos del país. Se ha escrito y diseñado un sistema basado en bash script que graba, recolecta y analiza estas transmisiones.
3. **Cámaras de Aeródromos**: Al parecer, por normas aeronáuticas, en este tipo de lugares es necesario tener imágenes en vivo cada cierto tiempo, lo que lo hace una excelente fuente de información a lo largo de chile.   

Lamentáblemente no todo es bueno. Este sistema presenta debilidades estadísticas: los sesgos. Al ser el arrebol un fenómeno temporal, presenta por definición, variabilidad. Esto induce sesgos en los datos que son reportados. En principio, los sesgos tendrían que auto regularse al verse incrementada la muestra, pero es necesario tener en cuenta esto en las primeras etapas de este desarrollo. Es por esto que he creado la categoría de 0.5, dado que no estoy seguro si ocurrió o no. 

---

## Clasificación y creación de una guía de referencia para clasificación de imágenes del arrebol

Dado que el arrebol son ventanas en el día donde puede pasar dicho fenómeno, basta que el/la observador/a aviste **a lo menos una** coloración de nubes **suficiente**, con una intensidad dada, para considerar que hubo arrebol. 
Dicha la anterior premisa, es necesario considerar que el arrebol es un **fenómeno caótico**, porque su aparición no solo depende de las condiciones metereológicas locales, sino que también de la geometría que poseen las nubes de camino a la dirección del sol. Por lo tanto, se considerarán los casos "simples" como una guía sobre cómo poder clasificar el fenómeno. Las escalas son las siguientes:

| Etiqueta | Significado | Criterio de clasificación |
|---|---|---|
| **1** | Sí hubo arrebol | El observador avista al menos una nube con coloración suficiente e intensidad clara, en la ventana del amanecer o atardecer |
| **0.5** | Más o menos / dudoso | Hay indicios de coloración, pero no se está seguro de si constituye arrebol |
| **0** | No hubo arrebol | No se observa coloración suficiente en las nubes durante la ventana correspondiente |

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

| # | Ciudad | Canal Youtube|
|---|--------|-------|
| 1 | Rapa Nui | [@MarejadasUV](https://www.youtube.com/@MarejadasUV) |
| 2 | ALMA | [@astroasahi](https://www.youtube.com/@astroasahi) |
| 3 | Mejillones | [@MarejadasUV](https://www.youtube.com/@MarejadasUV) |
| 4 | Vallenar | [@envivoimvallenar](https://www.youtube.com/@envivoimvallenar) |
| 5 | La Serena | [@LaSerenaDrone](https://www.youtube.com/@LaSerenaDrone) |
| 6 | Valparaíso | [@Manupuntocl](https://www.youtube.com/@Manupuntocl) |
| 7 | Santiago | [@SCLSkylineLive](https://www.youtube.com/@SCLSkylineLive) |
| 8 | San Antonio | [@sanantonioimagen](https://www.youtube.com/@sanantonioimagen) |
| 9 | Puerto San Antonio | [@sanantonioimagen](https://www.youtube.com/@sanantonioimagen) |
| 10 | El Quisco | [@sanantonioimagen](https://www.youtube.com/@sanantonioimagen) |
| 11 | San Fernando | [@bombatercera](https://www.youtube.com/@bombatercera) |
| 12 | Pichilemu | [@MarejadasUV](https://www.youtube.com/@MarejadasUV) |
| 13 | Curicó | [@vlnradio](https://www.youtube.com/@vlnradio) |
| 14 | Concepción | [@concecam](https://www.youtube.com/@concecam) |
| 15 | Punta Arenas | [@ExploraAustralis](https://www.youtube.com/@ExploraAustralis) |
| 16 | Puerto Williams | [@marcelogr250](https://www.youtube.com/@marcelogr250) |


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

https://aipchile.dgac.gob.cl/camara/

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

