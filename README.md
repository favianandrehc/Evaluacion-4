# Evaluacion-4


Integrantes del grupo:
-Favian Andre Hurtado Carlos.
-Alvaro Daniel Pino Chavez.
-Sandro Ronaldo Callañaupa Portal.
- nombre y apellidos

ACTIVIDAD 1

1. ¿Qué caracteriza a un algoritmo recursivo y cómo se relaciona con el principio Divide y Vencerás?

Un algoritmo recursivo es aquel que resuelve un problema llamándose a sí mismo una o varias veces, trabajando sobre una versión más pequeña del mismo problema hasta llegar a una condición que ya no necesita seguir llamándose caso base.

La recursividad está relacionada con el principio Divide y Vencerás, porque el problema principal se divide en subproblemas más pequeños. Cada llamada recursiva resuelve una parte del problema hasta que finalmente todas las soluciones parciales se combinan para obtener el resultado final.

En el caso de CampusNavigator IA, la recursividad puede utilizarse para contar automáticamente los puntos de control que un estudiante debe recorrer dentro del campus.

2. Algoritmo recursivo
   
def contar_pasos(n):
    if n == 0:      # Caso base
        return 0
    return 1 + contar_pasos(n - 1)

pasos = 6
print("Total de pasos:", contar_pasos(pasos))

Salida
Total de pasos: 6

3. Traza manual de ejecución

Caso de prueba:

ContarPasos(5)
Llamadas
ContarPasos(5)
↓
1 + ContarPasos(4)

ContarPasos(4)
↓
1 + ContarPasos(3)

ContarPasos(3)
↓
1 + ContarPasos(2)

ContarPasos(2)
↓
1 + ContarPasos(1)

ContarPasos(1)
↓
1 + ContarPasos(0)

ContarPasos(0)
↓
Retorna 0
Retorno de llamadas
ContarPasos(0) = 0

ContarPasos(1) = 1 + 0 = 1

ContarPasos(2) = 1 + 1 = 2

ContarPasos(3) = 1 + 2 = 3

ContarPasos(4) = 1 + 3 = 4

ContarPasos(5) = 1 + 4 = 5
Diagrama de llamadas
ContarPasos(5)
      |
ContarPasos(4)
      |
ContarPasos(3)
      |
ContarPasos(2)
      |
ContarPasos(1)
      |
ContarPasos(0)
      |
    Retorna 0
      ↑
    Retorna 1
      ↑
    Retorna 2
      ↑
    Retorna 3
      ↑
    Retorna 4
      ↑
    Retorna 5

Este ejemplo presenta 6 llamadas recursivas, cumpliendo con el requisito de al menos cinco niveles de ejecución.

4. Caso base, caso recursivo y criterio de finalización
Caso base

Cuando:

n == 0

Significa que ya no quedan puntos de control por revisar y la función retorna 0.

Caso recursivo

Mientras:

n > 0

La función cuenta un paso y vuelve a llamarse con un punto menos:

1 + ContarPasos(n - 1)
Criterio de finalización

La recursividad termina cuando el número de puntos de control llega a 0. En ese momento deja de realizar nuevas llamadas y comienza a retornar los resultados hasta completar el conteo total.

ACTIVIDAD 2

1. Vector de tiempos propuesto

Se considera el siguiente conjunto de tiempos estimados de desplazamiento entre diferentes puntos del campus (en minutos):

[12, 5, 18, 7, 3, 15, 10, 8]

2. Algoritmo recursivo utilizado

Para ordenar los tiempos de menor a mayor se utilizará el algoritmo recursivo Merge Sort, el cual divide el problema en partes más pequeñas, las ordena y luego combina los resultados.

def merge_sort(lista):
    if len(lista) <= 1:
        return lista

    medio = len(lista) // 2
    izquierda = merge_sort(lista[:medio])
    derecha = merge_sort(lista[medio:])

    return fusionar(izquierda, derecha)

def fusionar(izq, der):
    resultado = []
    i = j = 0

    while i < len(izq) and j < len(der):
        if izq[i] < der[j]:
            resultado.append(izq[i])
            i += 1
        else:
            resultado.append(der[j])
            j += 1

    resultado.extend(izq[i:])
    resultado.extend(der[j:])

    return resultado
3. Desarrollo paso a paso
División del problema

Vector original:

[12, 5, 18, 7, 3, 15, 10, 8]

Primera división:

[12, 5, 18, 7] [3, 15, 10, 8]

Segunda división:

[12, 5] [18, 7] [3, 15] [10, 8]

Tercera división:

[12] [5] [18] [7] [3] [15] [10] [8]

En este punto cada sublista contiene un solo elemento, por lo que ya se consideran ordenadas.

Combinación de resultados parciales

Se combinan las sublistas comparando sus elementos:

[12] + [5] → [5, 12]

[18] + [7] → [7, 18]

[3] + [15] → [3, 15]

[10] + [8] → [8, 10]

Luego:

[5, 12] + [7, 18] → [5, 7, 12, 18]

[3, 15] + [8, 10] → [3, 8, 10, 15]

Finalmente:

[5, 7, 12, 18] + [3, 8, 10, 15]

→ [3, 5, 7, 8, 10, 12, 15, 18]

4. Resultado final

El vector ordenado de menor a mayor es:

[3, 5, 7, 8, 10, 12, 15, 18]

5. Justificación de la estrategia recursiva

La estrategia recursiva es válida porque el problema principal de ordenar una lista puede dividirse en problemas más pequeños del mismo tipo. Cada sublista se ordena de forma independiente y posteriormente se combinan los resultados para obtener la lista completamente ordenada. La recursión termina cuando se alcanza el caso base, es decir, cuando la lista tiene uno o ningún elemento.

6. Análisis de eficiencia

El algoritmo Merge Sort tiene una complejidad temporal de O(n log n), lo que significa que su rendimiento es eficiente incluso cuando aumenta la cantidad de datos a ordenar. Su complejidad espacial es O(n), debido al uso de listas auxiliares durante el proceso de combinación. Por estas características, es una opción adecuada para ordenar tiempos de desplazamiento dentro de un campus universitario.


ACTIVIDAD 3













ACTIVIDAD 4 (Sustento técnico y cierre grupal)


Conclusión grupal:

El desarrollo de CampusNavigator IA permitió comprender cómo la combinación de diferentes estructuras y técnicas algorítmicas puede solucionar problemas reales dentro de un entorno educativo. La recursividad permitió plantear soluciones donde un problema puede dividirse en subproblemas más pequeños, facilitando procesos como el análisis de recorridos y el ordenamiento de información. Por otro lado, el uso de grafos permitió representar de manera eficiente la conexión entre los diferentes espacios del campus, como aulas, laboratorios y servicios, permitiendo aplicar algoritmos de búsqueda para encontrar rutas y recorridos adecuados.
La integración de estas técnicas demuestra la importancia de elegir correctamente una estrategia algorítmica según la necesidad del problema. Mientras la recursividad ayuda a organizar y procesar información de manera estructurada, los grafos permiten modelar relaciones entre elementos y realizar búsquedas optimizadas.

Pertinencia de la solución en un entorno educativo:

La solución propuesta es pertinente para una institución educativa porque facilita la orientación de estudiantes dentro del campus, reduciendo el tiempo necesario para encontrar ubicaciones específicas y mejorando la experiencia del usuario. Un sistema como CampusNavigator IA podría ayudar a estudiantes nuevos, visitantes y personal administrativo a encontrar rutas recomendadas considerando diferentes objetivos, como llegar rápidamente a un laboratorio, ubicar una oficina o explorar diferentes áreas del campus.
Como mejora para una segunda versión, se podrían incorporar datos en tiempo real, como cambios de disponibilidad de ambientes, congestión en determinadas zonas, integración con mapas digitales, reconocimiento de voz y personalización de rutas según las preferencias del usuario.

Organización de la entrega en GitHub y evidencias del README:

La entrega del proyecto será organizada en un repositorio de GitHub con una estructura clara que permita identificar cada parte del desarrollo. Se incluirán carpetas para almacenar el código fuente, documentación, diagramas y evidencias de ejecución.
En el archivo README se incluirán:
- Descripción general del proyecto CampusNavigator IA.
- Objetivo del sistema y problema que busca resolver.
- Explicación de los algoritmos utilizados (recursividad, ordenamiento,ETC).
- Casos de prueba y resultados obtenidos.
- Capturas de pantalla de la ejecución del sistema.
Esto permitirá que cualquier integrante del equipo o persona externa pueda comprender la solución, revisar su funcionamiento y conocer la justificación técnica de las decisiones tomadas.
