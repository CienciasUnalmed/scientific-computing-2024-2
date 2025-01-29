---
title: Introducción a Git
author: Diego Ospina
---

# El problema

<!-- pause -->

<!-- incremental_lists: true -->

- Ensayo para el colegio en 3 días

- Día 0: Escribimos el bosquejo

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
```

<!-- end_slide -->

- Día 1 en la mañana: Borramos algunas ideas del bosquejo pero lo guardamos por
  si acaso

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
```

<!-- end_slide -->

- Día 1 en la tarde: El tema que teníamos ya no nos gustó, pero uno nunca sabe
  si toca volver al tema viejo

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
```

<!-- end_slide -->

- Día 2 en la mañana: Por si acaso seguimos guardando todo

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
```

<!-- end_slide -->

- Día 2 en la tarde: Pulimos algunas comas y errores de redacción

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
  ensayo_nuevo_tema_mejor.doc
```

<!-- end_slide -->

- Día 3 en la mañana: Añadimos las imágenes

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
  ensayo_nuevo_tema_mejor_imágenes.doc
```

<!-- end_slide -->

- Día 3 en la noche: Creemos que el archivo ya está listo, y lo vamos a imprimir

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
  ensayo_nuevo_tema_mejor_imágenes.doc
  ensayo_nuevo_tema_mejor_imágenes_final.doc
```

<!-- end_slide -->

- 5 minutos después: La impresora sacó mal las imágenes así que movemos un poco
  las imágenes a ver si se arregla:

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
  ensayo_nuevo_tema_mejor_imágenes.doc
  ensayo_nuevo_tema_mejor_imágenes_final.doc
  ensayo_nuevo_tema_mejor_imágenes_final_final.doc
```

<!-- end_slide -->

- 5 minutos después: Las imágenes salieron bien esta vez, pero nos faltó una
  coma y un título en negrilla:

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
  ensayo_nuevo_tema_mejor_imágenes.doc
  ensayo_nuevo_tema_mejor_imágenes_final.doc
  ensayo_nuevo_tema_mejor_imágenes_final_final.doc
  ensayo_nuevo_tema_mejor_imágenes_final_final_este_si.doc
```

<!-- end_slide -->

...

<!-- end_slide -->

- Un par de ciclos de desesperación después...

<!-- pause -->

```
Ensayo/
  bosquejo_ensayo.doc
  ensayo.doc
  bosquejo_nuevo_tema.doc
  ensayo_nuevo_tema.doc
  ensayo_nuevo_tema_mejor_imágenes.doc
  ensayo_nuevo_tema_mejor_imágenes_final.doc
  ensayo_nuevo_tema_mejor_imágenes_final_final.doc
  ensayo_nuevo_tema_mejor_imágenes_final_final_este_si_ultimo.doc
  ensayo_nuevo_tema_mejor_imágenes_final_final_este_si_ultimo_ultimo.doc
  asdkjh.doc
  asdkjh2.doc
```

<!-- end_slide -->

# Problema de versionado

<!-- pause -->

<!-- incremental_lists: true -->

- Lo que estamos intentando hacer se llama "versionar" nuestro trabajo

- Etiquetas únicas para distinguir instantes de nuestro trabajo

- Pero, qué tan útil es realmente?

  - Entendemos qué había en `asdkjh.doc` que no había en el
    `ensayo_nuevo_tema_mejor_imágenes_final_este_si_ultimo.doc`?

  - Podemos comparar versiones de forma práctica?

  - Podemos repetir este proceso si cada archivo pesara 100 GB?

  - Qué pasa si tengo que trabajar con un compañero para hacer el ensayo?

<!-- incremental_lists: false -->

<!-- end_slide -->

# La realidad

<!-- pause -->

<!-- incremental_lists: true -->

- En un trabajo de colegio no importa mucho qué pase con las versiones de un
  trabajo

- Pero...

- Los programas también son archivos de texto!

- En un programa con más de 1000 archivos, es **vital** ser capaz de navegar,
  comparar y entender cada estado de nuestro trabajo para:

  - Identificar introducciones de bugs o errores

  - Coordinar cambios conflictivos

  - Revisar el trabajo de otros

  - Entender cómo históricamente se desarrolló una parte del proyecto

  - Otros...

<!-- incremental_lists: false -->

<!-- end_slide -->

# Solución: Git

<!-- pause -->

<!-- incremental_lists: true -->

- Git es un **sistema de control de versiones** que mantiene registro sobre
  cambios en **archivos**

- Fue creado por Linus Torvalds

- En 10 días

- Posiblemente el segundo proyecto open source más grande del mundo

<!-- incremental_lists: false -->

<!-- end_slide -->

# Nota

- Ideas > Comandos

- Usamos [`oh-my-git`](https://ohmygit.org/) con sus modos sandbox

<!-- end_slide -->

# Git

## Git essentials: Repositorio

- Es un espacio de almacenamiento en donde Git va a llevar seguimiento de todos
  los cambios a tus archivos.

```
Folder/
  .git/
  my_file1.txt
  my_file2.txt
```

Crea un subdirectorio `.git` que contiene todas las estructuras de datos
necesarias para guardar el historial de tu proyecto eficientemente.

<!-- pause -->

See: Empty sandbox

<!-- end_slide -->

## Git essentials: DAG

<!-- pause -->

<!-- incremental_lists: true -->

- Al trabajar con Git basamos nuestro versionado en un **DAG: Directed Acyclic
  Graph**, es decir, un **Grafo Acíclico Dirigido**

- La diferencia entre alguien capaz de hacer cosas avanzadas con Git, y alguien
  que no

- Al igual que cualquier grafo, está compuesto de vértices y aristas

  - Vértices: Son llamados **commits**

  - Aristas: Representan la relación de "parentesco", es decir, padre-hijo

<!-- incremental_lists: false -->

<!-- pause -->

See: Sandbox with three commits

<!-- end_slide -->

## Git essentials: Commit

<!-- pause -->

<!-- incremental_lists: true -->

Un commit es una **instantánea** de tu proyecto en un momento específico

- Representa un conjunto de cambios realizados en los archivos de tu proyecto
- Identificado por un hash único (SHA-1)
- Los commits suelen incluir un mensaje para explicar por qué se hizo el cambio

<!-- incremental_lists: false -->

<!-- pause -->

See (in Sandbox with three commits):

```
git log
git show <commit-sha>

mv you file1.txt # Change filename
git status
git add .
git commit -m "Cambio de nombre al archivo"
git status
git log
git show <commit-sha>

#Add to file1.txt: Nueva línea.
git status
git add file1.txt #OR git add .
git commit -m "Añadir una línea más"
git status
git log
git show <commit-sha>

git diff <last> <previous>
git diff <last> <second>
```

<!-- end_slide -->

## Git essentials: Branch

<!-- pause -->

<!-- incremental_lists: true -->

Una rama o branch es un **puntero a una serie de commits**

- Distinguimos la rama `main` como aquella donde (por convención) empieza el
  desarrollo
- Las **ramas de características** (feature branches) se crean para trabajar en
  nuevas funcionalidades o corregir errores sin afectar la rama main
  - Están pensadas para, en determinado momento, ser **fusionadas** a la rama
    principal `main`
- Las ramas permiten el desarrollo paralelo y la experimentación

<!-- incremental_lists: false -->

<!-- pause -->

Ejemplo: Proyecto de calculadora

- Suma (en main)
- Resta (pendiente)
- Multiplicar (pendiente)
- Dividir (pendiente)

Restar y multiplicar se pueden hacer en ramas separadas

<!-- pause -->

See (in Sandbox with three commits):

```
git switch not_main
git diff main

#Add to you: Línea en no_main.
git commit -am "Adición de línea en no_main"

git switch -c nueva_rama_desde_not_main

git switch main
git switch -c nueva_rama_desde_main

git branch -D nueva_rama_desde_not_main

#Change in file1: remove a dot
git commit -am 'Remoción de un punto'
```

<!-- end_slide -->

## Git essentials: Merge

<!-- pause -->

<!-- incremental_lists: true -->

El merge es la operación que combina cambios de una rama en otra.

- Puede ser un merge rápido (simple actualización de puntero) o un merge de tres
  vías (combinación de historiales divergentes).

<!-- incremental_lists: false -->

<!-- pause -->

See (in CLEAN Sandbox with three commits):

```
git switch no_main
```

<!-- end_slide -->

## Git essentials: Conflictos

<!-- pause -->

<!-- incremental_lists: true -->

Los conflictos ocurren cuando Git no puede fusionar automáticamente los cambios
de diferentes ramas.

- Deben resolverse manualmente editando los archivos en conflicto.

<!-- incremental_lists: false -->

<!-- end_slide -->

## Git collaborative: Remote

<!-- pause -->

<!-- incremental_lists: true -->

Un remoto es una **referencia a un repositorio alojado en otro lugar** (por
ejemplo, en GitHub o GitLab).

- Al remoto se le suele llamar `origin`.
- Comandos como `git push`` y `git pull\` interactúan con los remotos.

<!-- incremental_lists: false -->

<!-- end_slide -->

## Git collaborative: Clone

<!-- pause -->

<!-- incremental_lists: true -->

Clonar crea una copia local de un repositorio remoto, incluyendo todos los
commits, ramas y etiquetas.

- Comando: `git clone <repository-url>`

See: Later

<!-- incremental_lists: false -->

<!-- end_slide -->

## Git collaborative: Pull y fetch

<!-- pause -->

<!-- incremental_lists: true -->

- Pull: Trae cambios desde un repositorio remoto y los fusiona en tu rama local.
- Fetch: Recupera cambios de un remoto sin fusionarlos, permitiéndote
  inspeccionarlos primero.

<!-- incremental_lists: false -->

<!-- end_slide -->

## Git collaborative: Push

<!-- pause -->

<!-- incremental_lists: true -->

- Push envía tus commits locales a un repositorio remoto, actualizándolo.

<!-- incremental_lists: false -->

<!-- end_slide -->

# Por qué GitHub/Gitlab/cualquier otro?

<!-- pause -->

<!-- incremental_lists: true -->

- Centraliza el desarrollo en una "verdad"

- Añade características deseables: Revisiones, comentarios, PR, Drafts, entro
  otros.

<!-- incremental_lists: false -->

<!-- end_slide -->

# Flujo de trabajo en la vida real

## Desde cero

<!-- pause -->

<!-- incremental_lists: true -->

- Creación del repositorio local `git init`
- Adición de los archivos que lleva tu repositorio (código)
  `cp ../resources/readme.md . && cp ../resources/main.py .`
- Creación del repositorio remoto `gh repo create`
- Seguir desde el paso 2 de la siguiente slide.

<!-- incremental_lists: false -->

<!-- end_slide -->

<!-- pause -->

See: Repo en GitHub

## Desde un repositorio ya existente

<!-- pause -->

<!-- incremental_lists: true -->

- Clonar el repositorio `git clone <url>`
- Crear una rama desarrollo (feature branch) `git switch -c archivos_demo`
- Hacer tus cambios en el local y confirmarlos
  `git add . && git commit -m 'Adición de archivos de la presentación'`
- Empujar tus cambios desde el local al remoto (i.e. hacer push) `git push`
- Crear un PR desde GitHub
- Esperar revisiones y comentarios de tus pares

<!-- incremental_lists: false -->

<!-- end_slide -->

# Recursos adicionales

<!-- pause -->

<!-- incremental_lists: true -->

- Pro Git Book

  - Git avanzado: Cherry picking, rebase, reflog, squashing, etc

- Oh-my-git! (donde desarrollamos la presentación) - https://ohmygit.org/

- Learn Git Branching - https://learngitbranching.js.org/?NODEMO Alternativa
  online pero con menos características que Oh-my-git

- AI

- Conventional commits: https://www.conventionalcommits.org/en/v1.0.0/

  - Conventional comments: https://conventionalcomments.org/

<!-- incremental_lists: false -->

<!-- end_slide -->
