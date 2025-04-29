
# 🍬 Modelado de Golosinas y Acciones de Mariano

## Parte 1: Golosinas

Cada **golosina** tiene ciertas propiedades:  
- **Precio**  
- **Sabor**  
- **Peso inicial (en gramos)**  
- **Si contiene gluten o no**

Además, **todas** las golosinas **pierden peso** cuando reciben un **mordisco**, pero el modo en que pierden peso varía según el tipo.

---

### Bombón  
- **Precio**: $5  
- **Peso inicial**: 15g  
- **Sabor**: frutilla  
- **Libre de gluten** ✅  

**Mordisco:**  
Pierde un **20% del peso actual + 1g** extra.  
> Fórmula:  
```  
peso = (peso * 0.8) - 1
```

---

### Alfajor  
- **Precio**: $12  
- **Peso inicial**: 300g  
- **Sabor**: chocolate  
- **Libre de gluten** ❌  

**Mordisco:**  
Pierde un **20% del peso actual**.  
> Fórmula:  
```  
peso = peso * 0.8
```

---

### Caramelo  
- **Precio**: $1  
- **Peso inicial**: 5g  
- **Sabor**: frutilla  
- **Libre de gluten** ✅  

**Mordisco:**  
Pierde **1g** por mordisco.

---

### Chupetín  
- **Precio**: $2  
- **Peso inicial**: 7g  
- **Sabor**: naranja  
- **Libre de gluten** ✅  

**Mordisco:**  
Pierde el **10% del peso actual**, salvo que pese menos de 2g, en cuyo caso **no pierde nada**.

---

### Oblea  
- **Precio**: $5  
- **Peso inicial**: 250g  
- **Sabor**: vainilla  
- **Libre de gluten** ❌  

**Mordisco:**  
- Si pesa **más de 70g**, pierde **50% del peso**  
- Si pesa **70g o menos**, pierde **25% del peso**

---

### Chocolatín  
- **Peso inicial**: lo asigna el usuario  
- **Precio**: $0.50 por cada gramo de peso inicial  
- **Sabor**: chocolate  
- **Libre de gluten** ❌  

**Mordisco:**  
Pierde **2g** por mordisco.  
> **¡Importante!** El **precio es fijo**, calculado según el peso inicial.

---

### Golosina bañada  
Se compone de una **golosina base** + un **bañado de 4g**.  

- **Peso inicial**: peso de la base + 4g  
- **Precio**: precio de la base + $2  
- **Sabor**: igual al de la base  
- **Libre de gluten**: igual que la base  

**Mordisco:**  
- Se le da un mordisco a la golosina base.  
- Además, el bañado pierde peso:
  - Primer mordisco: pierde 2g
  - Segundo mordisco: pierde otros 2g

---

### Pastilla tutti-frutti  
- **Peso inicial**: 5g  
- **Libre de gluten**: configurable  
  - **Sí** → Precio: $7  
  - **No** → Precio: $10  
- **Sabor inicial**: frutilla  

**Mordisco:**  
Cambia de sabor en este ciclo:
```
frutilla → chocolate → naranja → frutilla ...
```

---

## Parte 2: Mariano

Mariano puede **comprar**, **probar**, **desechar** y **consultar** sobre las golosinas que tiene.  
Estas son las acciones que entiende:

### Operaciones básicas

- `comprar(unaGolosina)`  
  Agrega una golosina a su bolsa.

- `desechar(unaGolosina)`  
  Elimina una golosina de su bolsa.

- `probarGolosinas()`  
  Le da un mordisco a **todas** las golosinas en su bolsa.

---

### Consultas útiles

- `hayGolosinaSinTACC()`  
  ¿Hay alguna golosina sin gluten?

- `preciosCuidados()`  
  ¿Todas las golosinas cuestan **$10 o menos**?

- `golosinaDeSabor(unSabor)`  
  Devuelve **la primera** golosina con ese sabor.

- `golosinasDeSabor(unSabor)`  
  Devuelve **todas** las golosinas con ese sabor.

- `sabores()`  
  Devuelve todos los **sabores únicos** de las golosinas de la bolsa.  
  _Se recomienda usar conjuntos para evitar repetidos._  
  📎 [Guía sobre colecciones y closures](https://objetos1wollokunq.gitlab.io/material/guia-colecciones-basicas.pdf)

- `golosinaMasCara()`  
  Devuelve la golosina de **mayor precio**.

- `pesoGolosinas()`  
  Devuelve la **suma del peso** actual de todas las golosinas.

---

### Juliana

Juliana es la pareja de Mariano y tiene sus exigencias:

#### `golosinasFaltantes(golosinasDeseadas)`  
Devuelve las golosinas que Juliana quiere pero que **Mariano no compró**.

#### `gustosFaltantes(gustosDeseados)`  
Devuelve los **gustos deseados** por Juliana que **no están representados** en ninguna golosina de Mariano.


## Parte 3: Muhcas Golosinas
A partir de la solución desarrollada en las partes 1 y 2, hacer las modificaciones necesarias para que Mariano pueda comprar varios bombones, chocolatines, caramelos, alfajores, chupetines, obleas, golosinas bañadas y/o pastillas tuttifruti.

Resolver adecuadamente los casos en los que hay que pasar parámetros en la inicialización (el peso del chocolatín y la golosina a bañar).
