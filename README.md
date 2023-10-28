# -Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP
Elabora una herramienta destinada a la clasificación de temas y al análisis de la calidad del texto, haciendo uso de métricas como la diversidad léxica, la polaridad y el Índice de legibilidad Fernández Huerta que permita determinar si un texto es válido para su publicación en una revista independiente.

1. Introducción
El procesamiento de lenguaje natural (NLP) se ha convertido en una tecnología con alto impacto en nuestra vida cotidiana, redefiniendo la forma cómo consumimos información. Su capacidad para analizar y comprender grandes volúmenes de texto, extrayendo información valiosa sobre patrones lingüísticos, es esencial en la era digital actual.
Diversas industrias se han visto beneficiadas gracias al NLP. Por ejemplo, en el campo de la salud, se ha utilizado para analizar registros médicos y extraer información clínica relevante, impactando positivamente la atención al paciente. En la tecnología de la información, el NLP promueve motores de búsqueda más precisos y sistemas de recomendación más efectivos.
En el ámbito de los medios de comunicación, ha transformado la manera en que se produce y consume contenido. La automatización de contenido, como la creación de resúmenes de noticias o informes relevantes, ha impactado los tiempos de entrega de la información al público objetivo. La personalización de contenidos basada en preferencias garantiza que los lectores reciban información atractiva según sus gustos, mejorando así su experiencia.

2. Objetivo general
Elabora una herramienta destinada a la clasificación de temas y al análisis de la calidad del texto, haciendo uso de métricas como la diversidad léxica, la polaridad y el Índice de legibilidad Fernández Huerta que permita determinar si un texto es válido para su publicación en una revista independiente.

3. Descripción del proyecto
El proyecto se centra en utilizar el procesamiento de lenguaje natural (NLP) para llevar a cabo un análisis exhaustivo del texto de entrada. En un primer paso, se emplea un modelo de aprendizaje supervisado, concretamente una LSTM Bidireccional, que ha sido entrenado utilizando noticias del periódico El Tiempo desde el año 2020 hasta el 2023. Este modelo se utiliza para clasificar el tema del texto. A continuación, se evalúa la polaridad del texto en español con el objetivo de evitar cualquier sesgo en la publicación. Se buscan polaridades extremadamente positivas o negativas, lo que constituye el primer filtro de calidad.
Posteriormente, se procede a evaluar la calidad del texto desde diversas perspectivas. El proceso comienza con la medición del Índice de Legibilidad de Fernández Huerta, que establece un segundo filtro. Este índice permite determinar si el texto está dirigido a un público general o si, por el contrario, es demasiado sencillo o altamente especializado, como textos universitarios. El tercer filtro se basa en la diversidad léxica del texto, que debe superar un umbral del 45% para ser considerado apto.
Finalmente, el algoritmo toma la decisión de si el texto será publicado o no. Únicamente los artículos que logren superar con éxito todos estos filtros tendrán la oportunidad de ser publicados. Esto garantiza que los contenidos compartidos cumplan con altos estándares de calidad y sean adecuados tanto en términos de contenido como de legibilidad para la audiencia objetivo. Este enfoque integral asegura la idoneidad de los textos publicados.

![image](https://github.com/cesra147/-Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP/assets/99692504/5062d6b1-bae3-4faf-b065-c2c9e4f66bb4)

4. Preprocesamiento
   
Se llevaron a cabo dos etapas de preprocesamiento de texto para el idioma español. La primera etapa se centró en limpiar el texto de diversos elementos no deseados. Este proceso incluyó la eliminación de emojis, menciones de usuarios, hashtags, enlaces web, acentos y caracteres especiales. Además, se eliminaron números, saltos de línea y espacios en blanco adicionales. La limpieza se realizó mediante el uso de expresiones regulares y funciones proporcionadas por las bibliotecas re, demoji, unidecode y nltk.
La segunda etapa consistió en la lematización, un proceso que reduce las palabras a su forma base o lema. Esto implica expresar las palabras en su forma infinitiva, lo que facilita la reducción de la variación morfológica y simplifica el análisis del texto. Para llevar a cabo este proceso, se utilizó la biblioteca spaCy en el idioma español. El preprocesamiento se aplicó durante la fase de entrenamiento de los modelos supervisados y despliegue.

5. Base de datos modelo supervisado
   
Para entrenar el modelo supervisado de temas, se utilizó como fuente de datos el sitio web de noticias "El Tiempo", un diario colombiano que fue fundado el 30 de enero de 1911 por Alfonso Villegas Restrepo. En la actualidad, este periódico goza de una amplia circulación en Colombia y constituyó una invaluable base de datos para el presente estudio.
Las noticias recopiladas de "El Tiempo" se agruparon en las siguientes categorías: deportes, política, cultura, vida, economía y tecnosfera. Se recopilaron noticias publicadas durante los años comprendidos entre 2020 y 2023, obteniendo los siguientes volúmenes de datos por año:

• 2020: 3487 noticias.

• 2021: 8010 noticias.

• 2022: 8887 noticias.

• 2023: 2116 noticias.

A lo largo de estos años, se observó que la categoría de deportes presentó la mayor cantidad de noticias acumuladas, alcanzando un porcentaje del 47.99%. En segundo lugar, se ubicó la categoría de cultura, con un 34.07%, seguida de la política en tercer lugar, con un 7.70%. La categoría de economía ocupó el cuarto puesto, representando un 5.16% de las noticias acumuladas. En quinto lugar, se encontró la categoría de vida, con un porcentaje del 4.01%. Por último, la tecnosfera registró el porcentaje más bajo de noticias acumuladas, con un 1.07%.

![image](https://github.com/cesra147/-Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP/assets/99692504/8e215664-c43f-4707-8d0a-cdb472976381)

A continuación, se presenta el análisis de la frecuencia de palabras en todas las clases, expuesto en la tabla 1:

![image](https://github.com/cesra147/-Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP/assets/99692504/2fdfee91-7e6b-4cd1-a606-ec925ece0d75)

En relación con la frecuencia promedio, es notable que la clase "Vida" se destaca por presentar un valor más elevado en comparación con las demás categorías. Esto sugiere que la temática de "Vida" abarca un espectro lingüístico más amplio dentro de las noticias analizadas. Al analizar la frecuencia de las palabras por clase, se encontraron los siguientes resultados:

• En la categoría de "Cultura", la palabra más recurrente es "poder", con 17,366 apariciones.

• En la clase de "Deportes", la palabra más repetida es "partido", con 16,486 ocurrencias.

• En la categoría de "Economía", se destaca la palabra "poder", con 2,578 apariciones.

• En la clase de "Política", la palabra más frecuente es "Petro", con 3,568 ocurrencias.

• En la categoría de "Tecnosfera", la palabra más repetida es "nuevo", con 385 apariciones.

• Por último, en la clase de "Vida", la palabra "más" se presenta con mayor frecuencia, con 3,487 apariciones.
El conjunto de datos original presentaba un desequilibrio significativo, con una gran cantidad de observaciones en las clases "deportes" y "cultura", mientras que las clases "vida" y "tecnosfera" contaban con un número muy reducido de observaciones. La cantidad de observaciones para el período evaluado fue la siguiente: deportes (10,798), cultura (7,665), política (1,733), economía (1,160), vida (903) y tecnosfera (241). Para abordar este estudio, se aplicaron dos técnicas de muestreo: SMOTE y RandomUnderSampler. SMOTE (Synthetic Minority Oversampling Technique) [56] consiste en una técnica de sobremuestreo que genera nuevas observaciones sintéticas para la clase minoritaria a partir de las existentes. Por otro lado, Random Under Sampler es una técnica de submuestreo que reduce la cantidad de observaciones en la clase mayoritaria mediante la eliminación aleatoria de algunas observaciones. Se estableció un total de 1000 observaciones por clase para la etapa de balanceo.


6. Modelo supervisado para la detección de temas
La detección de temas es un conjunto de técnicas que tiene como objetivo identificar y comprender los temas o tópicos principales en un grupo de textos. Con la explosión de datos en la web, las redes sociales digitales y otras fuentes, resulta difícil y costoso analizar manualmente todo el contenido. Mediante la aplicación de técnicas de procesamiento de lenguaje natural (NLP), se pueden identificar automáticamente los temas principales en un conjunto de documentos, facilitando la búsqueda, el filtrado y la recuperación de información relevante.

6.1. Modelo implementado

Se desarrolló e implementó una red neuronal recurrente bidireccional (BRNN), esta estructura se compone de dos capas ocultas opuestas que se concatenan a la salida. Emplea dos direcciones, una dirección positiva (estados adelante) y otra dirección negativa (estados atrás). La salida de los dos estados no está conectada a las entradas de los estados de dirección opuesta; las dos neuronas direccionales no tienen interacciones. Se escogen dos redes de memoria a largo plazo (LSTM) debido a su capacidad de agregar o eliminar información a esta celda de estado usando una serie de compuertas (forget, update y output) que permiten discriminar entre la información relevante e irrelevante. Se emplea la herramienta Tensor Flow para su desarrollo.
Como primer paso se divide el conjunto de datos en entrenamiento y prueba, con un porcentaje de 20% para prueba siendo el tema la variable objetivo. Continuamente, el texto de entrada se transformó en identificadores de tokens numéricos organizándose en varios tensores antes de ingresar al modelo. Se aplicó la herramienta TensorFlow Hub que suministra un modelo de preprocesamiento que implementa esta transformación mediante operaciones TF de la biblioteca “TF.text”. El conjunto de entrenamiento y prueba se convierte a una secuencia tokenizada para su consumo.

Para la construcción del modelo se define una estructura con dos capas bidireccionales LSTM y una capa densa de decisión. Para evitar el sobre ajuste se emplea un Dropout de 0,5 y al ser una red de clasificación multi clase se aplica una función de pérdida Cross entropy. Se emplean 10 épocas para el entrenamiento en búsqueda de los mejores.

Se obtiene un Accuracy en entrenamiento de 97.29% y un Accuracy para pruebas de 82.58%.

![image](https://github.com/cesra147/-Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP/assets/99692504/f2fe91f4-b060-4311-a05c-1e5c902874cf)

![image](https://github.com/cesra147/-Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP/assets/99692504/9400918c-1c16-444d-a915-559bb12c7cef)

La gráfica 14 permite evidenciar un alto desempeño en el modelo entrenado para identificar categorías empleando una estructura bidireccional LSTM.

7. Clasificación de polaridad
   
Para analizar la polaridad de un texto en español, se ha implementado la librería "sentiment_analysis", que contiene un modelo previamente entrenado específicamente para realizar el análisis de sentimiento en español. Este proceso conlleva a la obtención de una probabilidad que indica la presencia de un sentimiento positivo o negativo en el texto.
Luego, se procede a realizar una clasificación categórica de esta probabilidad, que se traduce en las siguientes categorías: "Extremadamente Positivo", "Muy Positivo", "Positivo", "Neutral Positivo", "Neutro", "Neutral Negativo", "Negativo" o "Muy Negativo". Si el texto se clasifica como "Extremadamente Negativo" o "Extremadamente Positivo", se considera que no pasa el filtro de polaridad, ya que se interpreta como un indicativo de sesgo en la noticia.

9. Índice de Legibilidad Fernández Huerta

Métrica de legibilidad que se utiliza para evaluar la dificultad de un texto. Fue desarrollado por el lingüista español Antonio Fernández Huerta. El Índice FH se basa en el análisis de las características lingüísticas de un texto, principalmente la longitud de las oraciones y el número de sílabas en las palabras. Cuanto más cortas sean las oraciones y más simples sean las palabras (es decir, menos sílabas), más bajo será el valor del Índice FH, lo que indica que el texto es más fácil de comprender. Por otro lado, si las oraciones son largas y las palabras son complejas, el valor del Índice FH será más alto, lo que sugiere que el texto es más difícil de leer y comprender.

L= 206.84- 0.60P- 1.02F Donde L es la lecturabilidad; P, el promedio de sílabas por palabra; F, la media de palabras por frase

Primero se calcula este índice en el texto, continuamente se lleva a cabo una categorización del índice obtenido en las siguientes clasificaciones: "Muy fácil", "Fácil", "Algo fácil", "Normal", "Algo difícil", "Difícil" o "Muy difícil (universitario)". Si el resultado recae en "Muy fácil" o "Muy difícil", el texto no supera el filtro debido a que resulta excluyente para los lectores o su contenido no está adecuadamente estructurado para ser comparado con un texto de lectura básica.

9. Diversidad léxica y frecuencia Stopwords
    
Se realiza el cálculo de la diversidad léxica del texto de entrada, una métrica que evalúa la variedad de palabras únicas en relación con el número total de palabras. Esta medida se obtiene al dividir el número de palabras distintas por el tamaño total del vocabulario empleado en el texto. Una alta diversidad léxica indica una expresión rica y variada, mientras que una baja diversidad refleja la repetición frecuente de palabras, lo que puede sugerir una limitación en la sofisticación del lenguaje. Este valor se convierte en un porcentaje y, si supera el umbral del 45%, el texto pasa el filtro de diversidad léxica, lo que garantiza que tenga una redacción básica y estructurada.

10. Implementación
    
Se crea un script exclusivamente para la implementación, el cual carga el modelo supervisado previamente entrenado. El texto de entrada atraviesa una serie de etapas de preprocesamiento y filtrado, generando así un resultado. Este resultado detalla su rendimiento en cada fase y, al final, emite una decisión de aceptación o rechazo. Solo aquellos textos que logren superar todos los filtros serán considerados aptos.

![image](https://github.com/cesra147/-Clasificaci-n-y-An-lisis-L-xico-de-Art-culos-Utilizando-NLP/assets/99692504/b581cf7f-1f0f-413a-9019-49c544cd5c8e)

Grafica 6. Implementación de la herramienta desarrollada

11. Conclusiones

• A pesar del desbalanceo presente en la clase tecnosfera, a causa de la brevedad de sus noticias, los resultados del modelo BRNN-LSTM son favorables para la tarea de clasificación de textos de diferentes autores (clases). Los resultados del Accuracy para el conjunto de entrenamiento y conjunto de pruebas 97.29% y 82.58% respectivamente, refleja su alto rendimiento, lo cual indica que puede ser un modelo eficiente para el ejercicio de clasificación.

• El Índice de Legibilidad Fernández Huerta desempeña un papel relevante en este proyecto, ya que contribuye a la evaluación de la calidad de los textos analizados. Lo anterior teniendo en cuenta se busca garantizar que el contenido sea adecuado para el público objetivo. Según su complejidad se determinará si está dirigido a un público general o si su complejidad lo hace más adecuado para lectores con un nivel de educación superior.

• La diversidad léxica como herramienta para comprender la influencia de la publicación de textos y en la percepción que la audiencia sobre ellos. Para efectos de este proyecto la diversidad léxica requiere que un texto supere un umbral del 45%, siendo un filtro que garantiza la riqueza del lenguaje utilizado y la variedad de palabras en el texto. Esto no solo mejora la comprensión del contenido, sino que también enriquece la experiencia del lector al proporcionar una gama más amplia de palabras y conceptos.
