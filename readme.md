# PRUEBA INGENIERO DE DATOS - NEQUI

# Paso 1: Alcance del proyecto y captura de datos

Selección de dataset de Kaggle: NYC Yellow Taxi Trip Data

La Comisión de Taxis y Limusinas (TLC) de la ciudad de Nueva York (NYC) guarda datos de los servicios de todos sus taxis, este dataset solo cuenta con la información de los taxis amarillos que prestan sus servicio en el Estado de New York y su uso es por medio de paradas en la calle.

Con este dataset pueden implementarse diferentes casos de uso en análisis de datos, aprendizaje automatizado y visualización como:

Análisis y patrones de viaje: permite analizar los patrones de tráfico y viaje en el Estado, puede permitir comprender las horas pico, las rutas más frecuentes y las áreas de mayor demanda.

Predicción de tarifas y duración del viaje:utilizando características como la distancia, el tiempo y las condiciones del tráfico, se pueden construir modelos de aprendizaje automático para predecir la tarifa o duración del viaje, teniendo información útil tanto para conductores como pasajeros.

Optimización de rutas: con este conjunto de datos se pueden desarrollar algoritmos para encontrar las rutas más eficientes y rápidas del Estado de New York.

Análisis de congestión: se pueden utilizar los datos para identificar áreas de la ciudad que son propensas a la congestión del tráfico e intentar comprender las causas.

Segmentación de clientes: analizar los datos de viajes puede ayudar a segmentar a los pasajeros en diferentes categorías según sus patrones de viaje, lo que puede ser útil para la orientación de marketing.

Para este proyecto desarrollaré el primer caso de uso: análisis y patrones de viaje y solo utilizaré 2.000.000 de registros del Dataset

# Paso 2: Explorar y evaluar los datos, el EDA

Para la limpieza del dataset se tendrá en cuenta lo siguiente:
-Se realiza la busqueda de valores perdidos, no se encuentra ninguno.
-Se realiza la eliminación de resgistros duplicados. En total 124, pasando de quedando un total de 1.999.876
-Se limita el dataset a servicios de taxi en el Estado de Nueva York cuyas coordenadas (latitud,longitud) sea (40.5774, -74.15) & (40.9176,-73.7004). En total 38.880 registros, pasando de 1.999.876 a 1.960.996
-Se limita también el dataset por duración de los servicios inferior a 12 horas. En total 1310 , pasando de 1.960.996 a  1959686



# Paso 3: Definir el modelo de datos

MODELO DE DATOS CONCEPTUAL

Entidad principal: Viaje

Atributos:
VendorID (Id. de proveedor): Un código que indica el proveedor de TPEP que proporcionó el registro. (1 Tecnologías móviles creativas, 2 Verifone Inc.)
tpep_pickup_datetime (tpep_pickup_datetime): La fecha y la hora en que se activó el medidor.
tpep_dropoff_datetime (tpep_dropoff_datetime): La fecha y hora en que se desconectó el medidor.
Passenger_count (Número_de_pasajeros): El número de pasajeros en el vehículo. Este es un valor ingresado por el controlador.
Trip_distance (Distancia de viaje): La distancia del viaje transcurrido en millas reportada por el taxímetro.
Pickup_longitude (Recogida_longitud): Longitud donde se enganchó el medidor.
Pickup_latitude (Recogida_latitud): Latitud donde se enganchó el medidor.
RateCodeID (ID de código de tarifa): El último código de tarifa vigente al final del viaje. (1 Tarifa estándar, 2 jfk, 3 Newark, 4 Nasáu o Westchester, 5 Negotiated fare, 6 Group ride)
Store_and_fwd_flag (Store_and_fwd_flag): Esta bandera indica si el registro de viaje se mantuvo en la memoria del vehículo antes de enviarlo al proveedor, también conocido como "almacenar y reenviar", porque el vehículo no tenía conexión con el servidor. Y= viaje de almacenamiento y reenvío, N= no es un viaje de almacenamiento y reenvío
Dropoff_longitude (Dropoff_longitude): Representa la longitud donde el pasajero se baja del taxi al finalizar el viaje.
Dropoff_ latitude (Dropoff_ latitud): Representa la latitud donde el pasajero se baja del taxi al finalizar el viaje.
Payment_type (Tipo de pago): Un código numérico que significa cómo el pasajero pagó por el viaje. (1. Tarjeta de crédito, 2. Efectivo,  3. Sin cargo 4. Disputar 5. Desconocido, 6. viaje anulado
Fare_amount (Importe_tarifa): La tarifa de tiempo y distancia calculada por el taxímetro.
Extra (Extra): Varios extras y recargos. Actualmente, esto solo incluye. los cargos de $0.50 y $1 por hora pico y durante la noche.
MTA_tax (impuesto_MTA): Impuesto de 0.50 MTA que se activa automáticamente en función de la tarifa medida en uso.
Tip_amount (Tip_amount): Monto de la propina: este campo se completa automáticamente para las propinas de tarjetas de crédito. Las propinas en efectivo no están incluidas.
Tolls_amount (Importe_de_peaje): Importe total de todos los peajes pagados en el viaje.
Improvement_surcharge (Mejora_recargo): 0,30 recargo de mejora de los viajes evaluados en el descenso de bandera. el recargo por mejora comenzó a cobrarse en 2015.
Total_amount (Cantidad total): El monto total cobrado a los pasajeros. No incluye propinas en efectivo.

Elegí el conjunto de datos NYC Yellow Taxi Trip Data porque representa una fuente rica y diversa de información relacionada con la movilidad urbana y el transporte público en una de las ciudades más grandes del mundo. Esta elección se basa en varias razones:
Relevancia Urbana: El tráfico de taxis es un componente esencial del sistema de transporte en una ciudad tan poblada como Nueva York. Este conjunto de datos ofrece una visión detallada de los patrones de movimiento y las interacciones entre pasajeros y conductores en una configuración urbana única.
Gran Volumen de Datos: Con cerca de 12 millones de registros y una amplia gama de atributos, este conjunto de datos ofrece la oportunidad de realizar análisis exhaustivos y descubrir patrones que podrían influir en la toma de decisiones en áreas como la planificación del transporte y la movilidad.
Variedad de Atributos: El conjunto de datos incluye información sobre coordenadas geográficas, fechas y horas de recogida y entrega, tarifas, duración de viaje y más. Esta diversidad de atributos permite la realización de análisis multidimensionales que pueden arrojar luz sobre factores como la congestión del tráfico, las tendencias estacionales y la eficiencia del sistema de transporte.
En resumen, elegí este conjunto de datos debido a su relevancia en el contexto urbano, su amplitud y profundidad de información, así como las oportunidades que presenta para generar conocimientos significativos en el campo de la movilidad y el transporte.

# Paso 5: Completar la redacción del proyecto

¿Cuál es el objetivo del proyecto?
El objetivo de este proyecto es poder analizar los patrones de tráfico y viaje en el Estado de New York aplicando los conocimientos que tengo en el campo de la ingenieria de datos.

¿Qué preguntas quieres hacer?
-¿Cuáles son las horas pico con mayor demanda de taxis?
-¿Cuáles son las rutas más frecuentes?
-¿Cuáles son las áreas con mayor demanda de servicio de taxi?

¿Por qué eligió el modelo que eligió?
Elegí el modelo de análisis de agregación y visualización ya que la agregación permite obtener una comprensión rápida y concisa de los patrones y tendencias en los datos y con la visualización es más fácil identificar patrones y relaciones que podrían no ser evidentes en los datos sin procesar adicional permiten una interpretación más sencilla de los datos para aquellos que no están familiarizados con los detalles técnicos.

Incluya una descripción de cómo abordaría el problema de manera diferente en los siguientes escenarios:
Si los datos se incrementaran en 100x:
Si los datos se incrementaran en 100 veces su tamaño actual, podrían surgir problemas de rendimiento y escalabilidad. En este caso, consideraría utilizar tecnologías de almacenamiento y procesamiento distribuido como Google BigQuery, para manejar grandes volúmenes de datos de manera eficiente. También podría ser útil dividir el procesamiento en lotes más pequeños y paralelizar el proceso para aprovechar recursos adicionales.

Si las tuberías se ejecutaran diariamente en una ventana de tiempo específica:
Si las tuberías deben ejecutarse diariamente en una ventana de tiempo específica, consideraría programar y automatizar el proceso. Esto garantizaría que las tuberías se ejecuten de manera programada y puntual, lo que facilitaría la actualización constante de los datos y la generación de informes regulares.

Si la base de datos necesitara ser accedida por más de 100 usuarios funcionales:
Si se requiere un acceso a la base de datos por parte de más de 100 usuarios funcionales, consideraría la implementación de un sistema de gestión de bases de datos robusto y escalable, con políticas de seguridad y control de acceso para garantizar que los usuarios accedan solo a los datos que les corresponden y para prevenir problemas de congestión en la base de datos.

Si se requiere hacer analítica en tiempo real:
Para habilitar la analítica en tiempo real, consideraría agregar componentes de procesamiento en tiempo real a la arquitectura. Esto permitiría analizar y visualizar datos en tiempo real, lo que podría ser útil para tomar decisiones instantáneas basadas en la información más reciente.

En cuenta que cada uno de estos escenarios podría requerir ajustes y cambios en la arquitectura propuesta. La elección de las herramientas y tecnologías dependerá de las necesidades específicas y los requisitos del proyecto. Siempre es recomendable evaluar cuidadosamente las opciones disponibles y diseñar una arquitectura que satisfaga los objetivos y desafíos particulares de cada escenario.
