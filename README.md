# Simulador de Búfer en Python

Este programa implementa un simulador de búfer de entrada en Python, diseñado para procesar texto utilizando un sistema de punteros y un carácter especial (eof) como centinela.

## Descripción General

El programa simula un búfer de entrada con las siguientes características:
- Tamaño fijo de 10 caracteres
- Utiliza dos punteros para el procesamiento de lexemas
- Implementa un sistema de recarga automática del búfer
- Procesa el texto palabra por palabra (lexemas)

## Componentes Principales

### 1. Función `cargar_buffer`

```python
def cargar_buffer(entrada, inicio, tamano_buffer):
```

Esta función es responsable de:
- Cargar una porción de texto en el búfer desde la posición de inicio
- Añadir el centinela 'eof' si el búfer no está completamente lleno
- Retornar el búfer cargado

**Parámetros:**
- `entrada`: Lista de caracteres que contiene el texto a procesar
- `inicio`: Posición desde donde comenzar la carga
- `tamano_buffer`: Tamaño máximo del búfer (10 caracteres)

### 2. Función `procesar_buffer`

```python
def procesar_buffer(buffer, entrada, inicio, tamano_buffer):
```

Esta función maneja:
- El procesamiento de lexemas usando dos punteros
- La detección de espacios y el centinela 'eof'
- La recarga automática del búfer cuando es necesario

**Parámetros:**
- `buffer`: Búfer actual de caracteres
- `entrada`: Texto completo de entrada
- `inicio`: Posición actual en el texto de entrada
- `tamano_buffer`: Tamaño máximo del búfer

## Sistema de Punteros

El programa utiliza dos punteros principales:
1. `puntero_inicio`: Marca el inicio del lexema actual
2. `puntero_avance`: Se mueve a través del búfer para identificar el fin de cada lexema

## Proceso de Ejecución

1. Se inicializa el programa con un texto de entrada
2. Se carga el primer búfer de 10 caracteres
3. Los punteros comienzan a moverse por el búfer:
   - Al encontrar un espacio: se procesa el lexema actual
   - Al encontrar 'eof': se procesa el último lexema y termina
   - Al llegar al final del búfer: se recarga con nuevos caracteres
4. Se imprimen los lexemas procesados

## Ejemplo de Uso

```python
entrada = list("Esto es un ejemplo de entrada con eof")
inicio = 0
tamano_buffer = 10

buffer = cargar_buffer(entrada, inicio, tamano_buffer)
inicio = procesar_buffer(buffer, entrada, inicio, tamano_buffer)
```

### Salida Esperada
```
Lexema procesado: Esto
Lexema procesado: es
Lexema procesado: un
Lexema procesado: ejemplo
Lexema procesado: de
Lexema procesado: entrada
Lexema procesado: con
```

## Características Técnicas

- El búfer tiene un tamaño fijo de 10 caracteres
- Usa 'eof' como centinela para marcar el final del texto
- Procesa automáticamente palabras que cruzan límites del búfer
- Maneja eficientemente la memoria al cargar solo porciones del texto

## Consideraciones

- El programa asume que las palabras están separadas por espacios
- El centinela 'eof' marca el final del procesamiento
- La recarga del búfer es automática y transparente para el usuario
- Los lexemas se procesan y muestran en orden secuencial

## Limitaciones

- El tamaño del búfer es fijo (10 caracteres)
- Solo procesa texto con palabras separadas por espacios
- No maneja caracteres especiales o puntuación de manera especial
