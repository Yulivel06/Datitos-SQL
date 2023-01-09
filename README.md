
# Ejercicios de práctica-SQL

#### En esta sección, resolveremos algunos ejercicios para practicar nuestras habilidades de SQL

Los ejercicios son tomados de la pagina DataLemur: [Consulte Aquí](https://datalemur.com/)
 Puedes elegir que dificultad quieres resolver: fácil, medio, dificil. 

### Promedios móviles de tweets [Pregunta de entrevista de Twitter SQL]
La siguiente tabla contiene información sobre los tweets durante un período de tiempo determinado. Calcule el promedio móvil de 3 días de tweets publicados por cada usuario para cada fecha en que se publicó un tweet. Muestra la identificación del usuario, la fecha del tweet y los promedios móviles redondeados a 2 decimales.

**Suposiciones importantes** :

-   Las filas de esta tabla son _consecutivas_ y están ordenadas por fecha.
-   Cada fila representa un día diferente
-   No se cuenta un día que no corresponda a una fila de esta tabla. El día más reciente es la siguiente fila por encima de la fila actual.

Nota: El promedio móvil es una métrica que nos ayuda a analizar puntos de datos mediante la creación de una serie de promedios basados ​​en diferentes subconjuntos de un conjunto de datos. También se conoce como media móvil, media móvil, media móvil o media móvil.

Para resolver este ejercicio es importante conocer sobre las Funciones de ventanas deslizantes. :mag_right: 

(Ventanas deslizantes) Sliding windows 

Son funciones con las que podemos realizar calculos relativos a la fila actual de un conjunto de datos.
Podemos calcular: totales acumulados, sumas, conteos y promedios en cualqueir orden que necesitemos. 

Sintaxis   --- ROWS BETWEEN <star> AND <finish>

Palabras claves: 
PRECEDING y FOLLOWING: Para especificar el numero de filas antes o despues de la fila actual que desea incluir en el calculo. 
UNBOUNDED PRECEDING: indica que se desea incluir cada fila desde el principio del conjunto de datos en sus calculos 
UNBOUNDED FOLLOWING: indica que se desea incluir cada fila desde el final del conjunto de datos en sus calculos
CURRENT ROW: detener el calculo en la fila actual.

Asi: 
1. Debemos conococer el numero de twet por usuario para esto: 
 ``` sql
    SELECT 
    user_id, 
    tweet_date, 
    COUNT(tweet_id) AS total_tweet
  FROM tweets
  GROUP BY user_id, tweet_date
  ORDER BY user_id, tweet_date
```
