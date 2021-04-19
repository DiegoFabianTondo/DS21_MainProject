# DS21_MainProject
Repositorio para mentoria de proyecto en DiploDatos 2021, Famaf, UNC.

## Título
GAP: Gestión Automática de Pedidos de Combustibles Líquidos basada en telemetría de inventarios.

## Descripción
La logística en las cadenas de suministro de combustibles líquidos, lubricantes y otros líquidos en los segmentos de Transporte, Industría, Minería, Agricultura, Construcción, Telecomunicaciones y Oil&Gas ha sido desde siempre un factor crítico en la operación diaria de los negocios, en el manejo de sus costos, y en el acceso a opciones de provisión. 

En general, los centros operativos donde se almacenan combustibles, lubricantes y otros líquidos para la operación (estaciones de servicio privadas) son abastecidos a demanda del consumidor, de acuerdo a información que es relevada manualmente, y con solicitudes informales entre encargados y proveedores. Esto genera numerosos conflictos:
- Quiebres de stock
- No se pueden planificar eficientemente las entregas
- Escasa posibilidad de administrar riesgos y costos
- Ausencia de alternativas
- Imposibilidad de acceder a opciones para la diversificación de la matriz energética
- Informalidad administrativa y ausencia de procedimientos certificables
- Marcos regulatorios, apoyos económicos y subsidios, sin información cierta
- Desconocimiento del comportamiento y prácticas del consumidor en materia energética

Con el apoyo de entidades privadas, y sobre todo por el departamento de Desarrollo de Negocios de YPF en el marco de un proyecto llamado “Control y Trazabilidad”, se esta logrando disponer de datos por telemetría de inventarios de combustibles líquidos, lubricantes y otros liquidos en segmentos de negocios que requieren alcanzar metas estrictas de eficiencia y de diversificación energética en búsqueda de la sustentabilidad social y económica del país. 

El objetivo de la Mentoría y del proyecto, es utilizar los historiales de los inventarios de tanques para implementar modelos de estimaciones futuras (forecasting) y generar notificaciones que automaticen el pedido de suministro a los proveedores (GAP) con cierta antelación. Alcanzar momentos óptimos de aprovisionamiento, con el uso eficiente de las infraestructuras disponibles y de las cisternas de reparto. 
Este tema es interesante porque…
Los datos de telemetría de tanques de almacenamiento y su análisis inmediato abren la puerta a solucionar problemas que hasta ahora era poco manejables. Problemas que restringían la posibilidad de alcanzar objetivos estrictos en materia energética y de competitividad. 

## Este proyecto puede ayudar a que:

- La operaciones no sufran quiebres de stock 
- Las operaciones logren administrar costos y ser mas competitivos
- Los proveedores puedan planificar una logística de distribución mas eficiente
- Se pueda trabajar en marcos regulados y controlados
- Se entienda el comportamiento de consumo y prácticas de los negocios
- Se incentive la diversificación energética hacia otro tipos de combustibles

## Trataremos de responder algunas de las siguientes preguntas:

En el proceso de entender el problema y llegar al objetivo planteado, se desea responder las siguientes preguntas:
- Para qué podría servirnos cada atributo del dataset?. 
- Podemos prescindir de cierta información?. Podemos filtrar datos de algún tipo de sitio?.
- Cómo describimos estadísticamente la forma en que se administran los inventarios?.
- Qué estadístico podríamos usar para estimar los inventarios de un centro operativo?.
- Es posible parametrizar patrones y descriptores de acuerdo a ciertas features?.
- Cuáles son las features mas relevantes de acuerdo al objetivo del proyecto?.
- Cuáles son los patrones de consumo por segmento, por sitio, por infraestructura?.
- Hay alguna correlación entre los inventarios y otras features del centro operativo?.
- Cómo se debe agregar la información de múltiples tanques de un mismo producto?.
- Hay estacionalidad y/o tendencias?.
- Se podrá lograr una generalización o deberemos analizar cada centro operativo?.
- Hay anomalías en los inventarios?, los datos son validos para continuar?.
- Cómo solucionamos que la información sea intermitente, tiene ruido o datos erróneos?.
- Qué otras notificaciones podemos generar de acuerdo al análisis de inventarios?.
- Cómo podríamos detectar transacciones de consumo?.
- Cómo podríamos detectar transacciones de abastecimientos?.
- Qué modelo es el mas eficiente para estimar inventarios en el lapso del día?.
- En qué momento será necesario abastecer el centro operativo?, con qué cantidad?.
- Cuál es el momento óptimo de aprovisionamiento del centro operativo?.
- Cómo podríamos considerar el tipo de cisterna de distribución en la recomendación?.
- Cómo se implementaría el modelo en un arquitectura de ETLs por Batch?.

## Los datos
El dataset esta conformado por el historial de inventarios de tanques en sitios de diferentes empresas. Se trata de información real de centros operativos distribuidos en Argentina y algunos otros países. Los historiales son del primer trimestre de 2021. Los datos provienen de sensores de nivel magnetostrictivos colocados en los tanques de los centros operativos. Los datos son almacenados en servidores sin demasiada curación. Pueden contener errores. Puede haber datos faltantes en algunos casos.

Si querés inspeccionar el conjunto de datos, lo encontrarás en: 
https://drive.google.com/drive/folders/11SDpN-6aDr90FCllVWB_cZ2zy8G9KZ_7?usp=sharing

El dataset esta conformado por los siguientes datos:
- id: número único de identificación de historial 
- id_equipo: número único de identificación de centro operativo
- id_tanque: número único de identificación de tanque
- volumen: volumen medido por el sensor 
- temperatura: temperatura del líquido en la medición
- codigo: tipo de medición
- vbat1: tensión de las baterías del sensor
- vbat2: tensión de pulso de medición
- fuel_level_dmm: altura del líquido
- water_level_dmm: altura de agua al fondo del tanque
- water_volume_lts: volumen de agua al fondo del tanque
- producto: id único del producto en los tanques del centro operativo
- temp5: temperatura dentro del sensor en la posición 5 dentro de la sonda
- temp4: temperatura dentro del sensor en la posición 4 dentro de la sonda
- temp3: temperatura dentro del sensor en la posición 3 dentro de la sonda
- temp2: temperatura dentro del sensor en la posición 2 dentro de la sonda
- temp1: temperatura dentro del sensor en la posición 1 dentro de la sonda (extremo superior)
- id_empresa: identificador único de empresa
- current_firmware: identificador de firmware del sistema de telemetría
- id_canal: identificador único de canal distribuidor del sistema de telemetría
- id_industria: identificador de tipo de segmento de mercado
- industria: descripción del segmento de mercado
- capacidad: capacidad del tanque medido
- alarma: nivel de alarma de bajo nivel configurada por el encargado del centro operativo
- nombre_producto: nombre del producto que contiene el tanque
- coef_var_vol: coeficiente de variación volumétrica por temperatura 
- density: densidad del producto
- timestamp: fecha y hora de la medición

## Hitos de la mentoría
**Entrega 6/6 - Práctico de análisis y visualización**, que consistirá en racionalizar los datos involucrados en el dataset. Visualizar series temporales agregadas por diferentes objetos de agrupación. Tratamiento de outliers. Visualizar patrones de administración de inventarios por producto en centros operativos. Descubrir diferencias en los patrones de acuerdo al tipo de segmento. Estudio de teoría para análisis estadístico de series temporales. Analizar la correlación de los patrones de consumo de acuerdo al segmento, infraestructura, producto, etc. Analizar la matriz de correlación cruzada entre las diferentes features del dataset. Identificar los modelos probabilísticos mas adecuados para describir el comportamiento de consumo y los patrones de administración de inventarios. Probar test de hipótesis del modelo seleccionado como descriptor. Probar modelos parametrizados con features seleccionadas para estimar un inventario en un momento aleatorio en un centro operativo.

**Entrega 4/7 - Práctico de análisis exploratorio y curación de datos**, que consistirá en detectar información faltante, datos erróneos y selección de features importantes. Limpieza, agregaciones y rolling windows para simplificación de las series temporales. Agregaciones y transformaciones importantes. Normalización. Detección de estacionalidad y tendencias. Analizar si es posible la generalización de las series de acuerdo a ciertos parámetros. Fill y Drop de datos en las series de acuerdo a criterios de validación de otros campos. 

**Entrega 4/7 - Video de presentación del proyecto y dataset**

**Jornada 17/7 - Discusión sobre presentación de proyectos y datasets**

**Entrega 15/8 - Práctico de introducción al aprendizaje automático**, que consistirá en realizar feature engineering. Generar un dataset mínimo de entrenamiento para detectar datos erróneos. Realizar clasificación de tipo de segmento de acuerdo a los patrones de consumo. Realizar regresiones con diferentes modelos simples para estimar inventarios en lapsos cortos de tiempo. Selección de las métricas mas adecuadas para las estimaciones temporales que se van a realizar. 

**Entrega 12/9 - Práctico aprendizaje supervisado**, que consistirá en estudiar y probar modelos auto-regresivos o por descomposición de series para realizar forecasting de los inventarios en lapsos de tiempo superiores. Pruebas de hipótesis sobre los modelos a implementar y las métricas seleccionadas de evaluación. Pruebas de hipótesis sobre estacionalidad y tendencias. Selección de mejor modelo para forecasting y conclusiones sobre la manera en que se debería implementar el modelo en entorno productivos, sea tipo instancia a entrenar o modelo general con hiper-parámetros. 

*Extras: Jugar con RNN o CNN para forecasting de series temporales. Comparar con los modelos anteriores.* 


**Entrega 2/10 -  Práctico aprendizaje no supervisado**, que consistirá en aplicar diferentes modelos de clustering para jugar sobre las series históricas y sacar conclusiones. Aplicación de PCT en las series temporales, obtener conclusiones y comparar con las decisiones tomadas respecto del feature engineering realizado previamente. Encontrar un método para detectar anomalías en los datos. 

*Extra: Detección de abastecimientos con modelos semi-supervisados.*
*Extra: Detección de consumos con modelos semi-supervisados.*

**Entrega 22/10 - Video de presentación de mentoría**

**Jornadas 12/11 y 13/11 - Presentación de mentorías**
