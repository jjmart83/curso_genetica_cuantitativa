Práctica 1: Estimación de Heredabilidad
Horario: Lunes, 15:00 - 18:00
Repositorio: Aquí iría el enlace a tu repositorio

1. Objetivos de la Práctica
Aplicar métodos estadísticos para estimar la heredabilidad de un rasgo.
Utilizar la regresión padre-hijo y ANOVA en datos reales o simulados.
Interpretar los resultados estadísticos y discutir su relevancia biológica.
2. Actividades
2.1. Introducción al Software Estadístico
R y RStudio: Breve tutorial sobre cómo:
Instalar y/o abrir RStudio.
Crear y ejecutar scripts .R.
Instalar y cargar paquetes relevantes, como dplyr, ggplot2 o cualquier otro.
```r

Ejemplo de instalación de paquetes (si es necesario):
install.packages(c("dplyr", "ggplot2"))
library(dplyr) library(ggplot2) ```

2.2. Análisis de Datos: Carga y Manipulación
Carga de datos (archivos .csv en la carpeta datos/, o datos simulados).
Manipulación básica: Ver estructura (str()), resumen (summary()), manejo de valores ausentes.
```r

Opción A: Cargar datos desde un archivo CSV
datos <- read.csv("datos/heredabilidad.csv")
Opción B: Simulación de datos (ejemplo)
set.seed(123) n <- 100 Padre <- rnorm(n, mean = 100, sd = 15) # Valores del rasgo en los padres heredabilidad_verdadera <- 0.5 # Valor teórico (ejemplo) error <- rnorm(n, mean = 0, sd = 10) # Variabilidad ambiental Hijo <- heredabilidad_verdadera * Padre + error

datos <- data.frame(Padre, Hijo)

Vista previa
head(datos) ```

2.3. Realización de Regresión y ANOVA
Regresión padre-hijo: La pendiente (slope) es una aproximación a la heredabilidad.
```r modelo <- lm(Hijo ~ Padre, data = datos) summary(modelo) ```

ANOVA: Para evaluar la significancia del modelo:
```r anova_modelo <- anova(modelo) anova_modelo ```

Observa el valor p y la F para juzgar la relevancia estadística.

2.4. Interpretación de Resultados
Pendiente (slope) ≈ heredabilidad (en un modelo ideal).
Coeficiente de determinación (R²): proporción de varianza explicada.
Significancia estadística: valoremos la p y el intervalo de confianza.
3. Metodología
Trabajo Colaborativo:
Grupos pequeños para fomentar discusión e intercambio de ideas.
Asesoría Personalizada:
El instructor pasa por los grupos para ayudar en el análisis.
Discusión Grupal Final:
Cada grupo comparte sus hallazgos y discute posibles limitaciones del método.
4. Recursos Necesarios
Computadoras con R instalado.
Conjuntos de datos (reales o simulados).
Esta Guía como referencia.
5. Cronograma de la Sesión
15:00 - 15:15: Introducción a R y paquetes.
15:15 - 16:00: Carga y exploración de datos.
16:00 - 16:45: Ajuste del modelo (regresión) + ANOVA.
16:45 - 17:30: Interpretación y conclusiones preliminares.
17:30 - 18:00: Discusión grupal y resolución de dudas.
6. Ejemplo de Visualización (Opcional)
Para enriquecer la práctica, podemos trazar la relación Padre-Hijo:

```r ggplot(datos, aes(x = Padre, y = Hijo)) + geom_point(alpha = 0.6, color = "blue") + geom_smooth(method = "lm", color = "red", se = TRUE) + labs(title = "Regresión Padre-Hijo", x = "Rasgo en el Padre", y = "Rasgo en el Hijo") ```

Esto ayudará a comprender visualmente la correlación entre ambas variables.
