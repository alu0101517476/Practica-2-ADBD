# Practica-2-ADBD

# 📘 Práctica 2: Modelo Entidad-Relación. Farmacia  
---

## 🏫 Información Académica

| **Universidad**        | Universidad de La Laguna |
|-------------------------|--------------------------|
| **Facultad**           | Escuela Superior de Ingeniería |
| **Asignatura**         | Administración de Bases de Datos |
| **Curso académico**    | 2025 / 2026 |
| **Práctica**           | Nº 2 – Modelo Entidad-Relación |

---

##  👥 Miembros del Grupo

| **Nombre**           | **Correo**                               |
|----------------------|-------------------------------------------|
| Alba Pérez Rodríguez | alu0101513768@ull.edu.es          |
| Eric Bermúdez Hernández  | alu0101517476@ull.edu.es       |
---
---


## 📑 Índice

1. [Introducción](#1-introducción)  
2. [Entidades y atributos](#2-entidades-y-atributos)  
   2.1 [💊 Medicamento](#21-medicamento)  
   2.2 [🏭 Laboratorio](#22-laboratorio)  
   2.3 [🗂️ Familia](#23-familia)  
   2.4 [👤 Cliente](#24-cliente)  
   2.5 [🩺 Enfermedad](#25-enfermedad)  
3. [Relaciones](#3-relaciones)  
   3.1 [Relación Medicamento - Laboratorio](#31-relación-medicamento---laboratorio)  
   3.2 [Relación Medicamento - Familia](#32-relación-medicamento---familia)  
   3.3 [Relación Medicamento - Cliente](#33-relación-medicamento---cliente)  
   3.4 [Relación Familia - Enfermedad](#34-relación-familia---enfermedad)  
   3.5 [Relación Medicamento - Tipo de medicamento](#35-relación-medicamento---tipo-de-medicamento)  
   3.6 [Relación Cliente - Tipo de cliente](#36-relación-cliente---tipo-de-cliente)  
4. [Restricciones semánticas](#4-restricciones-semánticas)  



## 1. Introducción.

En este documento se presenta un **modelo entidad-relación (E-R)** diseñado para gestionar la información de una **farmacia**.  
El objetivo del modelo es organizar de forma eficiente los datos de clientes, medicamentos, laboratorios, familias y enfermedades, así como las interacciones entre ellos.  

## 2. Entidades y atributos.

### 2.1 💊 Medicamento  
**Descripción:** Representa cada uno de los medicamentos que ofrece la farmacia, incluyendo su forma, condiciones de venta y características básicas para su identificación y control.

**Atributos:**  

| **Atributo** | **Descripción** | **Ejemplo** |
|--------------|-----------------|-------------|
| **Código medicamento (PK)** | Identificador único para cada medicamento. Puede coincidir con un código de barras. | `MED-001` |
| **Nombre** | Nombre comercial del medicamento. | `Paracetamol 500mg` |
| **Tipo de medicamento** | Atributo compuesto que indica la forma farmacéutica o condición de venta: **jarabe, pomada, pastillas, con receta, sin receta**. | `Comprimidos`, `Con receta` |
| **Unidades en stock** | Número de unidades disponibles en la farmacia. | `250` |
| **Unidades vendidas** | Cantidad de unidades vendidas en un periodo. | `120` |
| **Precio** | Precio unitario de venta. | `5.75 €` |

---

### 2.2 🏭 Laboratorio  
**Descripción:** Entidad que representa a los laboratorios que producen o distribuyen los medicamentos.  

**Atributos:**  

| **Atributo** | **Descripción** | **Ejemplo** |
|--------------|-----------------|-------------|
| **Código laboratorio (PK)** | Identificador único del laboratorio. | `LAB-003` |
| **Nombre** | Nombre del laboratorio. | `Laboratorios Genéricos S.A.` |
| **Teléfono** | Número de contacto. | `+34 912345678` |
| **Dirección postal** | Dirección física del laboratorio. | `Calle Mayor 45, Madrid` |
| **Fax** | Medio de comunicación alternativo. | `+34 912345679` |
| **Persona de contacto** | Responsable asignado para la comunicación. | `Dr. Carlos Pérez` |

---

### 2.3 🗂️ Familia  
**Descripción:** Representa las categorías terapéuticas o de uso de los medicamentos, permitiendo agruparlos según la enfermedad o afección que tratan.  

**Atributos:**  

| **Atributo** | **Descripción** | **Ejemplo** |
|--------------|-----------------|-------------|
| **Nombre familia (PK)** | Identificador único de la familia de medicamentos. | `Analgésicos` |

---

### 2.4 👤 Cliente  
**Descripción:** Representa a las personas que compran medicamentos en la farmacia, diferenciando entre quienes pagan al contado y quienes tienen acuerdo de crédito.

**Atributos:**  

| **Atributo** | **Descripción** | **Ejemplo** |
|--------------|-----------------|-------------|
| **DNI (PK)** | Identificador único del cliente. Garantiza que no existan duplicados. | `12345678A` |
| **Nombre** | Nombre y apellidos del cliente. | `María López García` |
| **Tipo de cliente** | Define si el cliente es **con crédito** (tiene acuerdo de pago) o **sin crédito** (paga al contado). | `Con crédito` |
| **Datos bancarios** | Obligatorio solo para clientes con crédito. Se refiere a la cuenta bancaria asociada. | `ES91 2100 0418 4502 0005 1332` |
| **Fecha** | Fecha de alta del crédito. Solo para clientes con crédito. | `2023-06-01` |

---

### 2.5 🩺 Enfermedad  
**Descripción:** Representa las enfermedades o afecciones que pueden ser tratadas con los medicamentos de la farmacia, facilitando la relación entre tratamiento y paciente.

**Atributos:**  

| **Atributo** | **Descripción** | **Ejemplo** |
|--------------|-----------------|-------------|
| **Nombre enfermedad (PK)** | Identificador único de la enfermedad. | `Migraña` |



---

## 3. Relaciones.
En este apartado se describen de forma detallada las **relaciones** entre las entidades presentes en el diagrama.  
Cada relación se explica indicando su **participación**, **cardinalidad**, **interpretación** e **importancia en el modelo**.


### 3.1. Relación Medicamento - Laboratorio.
- **Participación:**  
  - Un **medicamento** puede estar relacionado con **uno o varios laboratorios**.  
  - Un **laboratorio** puede producir o distribuir **uno o varios medicamentos**.  

- **Cardinalidad:** `(N, M)`  

- **Interpretación:**  
  Esta relación refleja el vínculo de producción o distribución. Un medicamento concreto (ejemplo: Paracetamol 500mg) puede provenir de distintos laboratorios, lo que permite tener opciones en caso de falta de suministro de uno de ellos. A su vez, un laboratorio no se limita a un solo producto, sino que fabrica o distribuye distintos medicamentos que luego llegan a la farmacia. 

- **Importancia en el modelo:**  
  Garantiza que se pueda identificar de qué laboratorio proviene cada medicamento, dato clave para la trazabilidad y para la gestión de proveedores.  

---

### 3.2. Relación Medicamento - Familia.

- **Participación:**  
  - Cada **medicamento** pertenece a **una única familia**.  
  - Una **familia** puede agrupar **muchos medicamentos**.  

- **Cardinalidad:** `(1, N)`  

- **Interpretación:**  
  Esta relación permite clasificar los medicamentos en categorías terapéuticas. Por ejemplo, la familia Analgésicos puede contener medicamentos como Ibuprofeno 600mg, Paracetamol 500mg y Metamizol. Esa clasificación facilita ofrecer al cliente alternativas de la misma familia si un medicamento específico no está disponible en stock. 

- **Importancia en el modelo:**  
  Es fundamental para organizar el catálogo de la farmacia y mantener coherencia en la clasificación de productos.
---

### 3.3. Relación Medicamento - Cliente.
- **Participación:**  
  - Un **cliente** puede comprar **uno o varios medicamentos**.  
  - Un **medicamento** puede ser comprado por **muchos clientes**.  

- **Cardinalidad:** `(1, N)`  

- **Atributos de la relación:**  
  - **Fecha de compra**:  indica el día en que se realizó la compra.
  - **Número de medicamentos comprados**  : cantidad de unidades de ese medicamento adquiridas en la compra.

- **Interpretación:**  
  Esta relación modela la transacción de venta entre la farmacia y sus clientes. Permite registrar de manera detallada qué medicamentos compró un cliente, cuántos y en qué fecha. Por ejemplo, el cliente María López (DNI: 12345678A) puede comprar 2 cajas de Ibuprofeno 600mg el 15/05/2023.

- **Importancia en el modelo:**  
  Vincula la gestión de inventario con la de clientes, permitiendo controlar ventas y stock.  

---

### 3.4. Relación Familia - Enfermedad.
- **Participación:**  
  - Una **familia** puede tratar **varias enfermedades**.  
  - Una **enfermedad** puede ser tratada por **diferentes familias**.  

- **Cardinalidad:** `(N, M)`  

- **Interpretación:**  
  Esta relación vincula los medicamentos con su finalidad terapéutica. Por ejemplo, la familia Antibióticos puede tratar tanto infecciones urinarias como bronquitis. A su vez, la enfermedad Migraña puede ser tratada con medicamentos de la familia Analgésicos y también con los de la familia Antimigrañosos.

- **Importancia en el modelo:**  
  Proporciona la lógica médica del sistema: relaciona la clasificación de medicamentos con las enfermedades que pueden tratarse, lo cual ayuda tanto a nivel de consulta como de gestión de inventario.

---

### 3.5. Relación Medicamento - Tipo de medicamento.
- **Participación:**  
  - Todo **medicamento** debe clasificarse en **un único tipo**.  
  - Tipos: *Venta libre* o *Con receta*.  
  
- **Interpretación:**  
  Esta relación permite diferenciar los medicamentos que requieren receta médica de los que se pueden vender libremente. Por ejemplo, Paracetamol 500mg puede ser “Venta libre”, mientras que Amoxicilina 875mg sería “Con receta”.

- **Importancia en el modelo:**  
  Asegura el cumplimiento legal en la dispensación de medicamentos.  

---

### 3.6. Relación Cliente - Tipo de cliente
- **Participación:**  
  - Todo **cliente** pertenece a **un único tipo**.  
  - Tipos: *Con crédito* o *Sin crédito*.  

- **Interpretación:**  
  Diferencia la forma de pago de los clientes.  
  - *Sin crédito*: pago al contado.  
  - *Con crédito*: pago a fin de mes, con datos bancarios y fecha de alta.  

- **Importancia en el modelo:**  
  Permite gestionar tanto ventas al contado como ventas a crédito, controlando la facturación y cobros pendientes.  

--- 

---

## 4. Restricciones semánticas  

Además de las entidades y relaciones definidas, el modelo incorpora una serie de restricciones que garantizan la coherencia de los datos y reflejan las reglas de negocio de la farmacia:

1. **Especialización de Cliente**  
   - Todo cliente debe pertenecer **únicamente a uno de los dos tipos**: *Con crédito* o *Sin crédito*.  
   - Si un cliente es *Con crédito*, debe registrar obligatoriamente los **datos bancarios** y la **fecha de alta del crédito**.  

2. **Especialización de Medicamento**  
   - Todo medicamento debe clasificarse **exclusivamente** como *Con receta* o *Venta libre*.  
   - No se admite la existencia de medicamentos fuera de estas dos categorías.  

3. **Relación Medicamento – Familia**  
   - Cada medicamento debe estar asociado a **exactamente una familia**.  
   - Una familia puede agrupar múltiples medicamentos, pero un medicamento no puede pertenecer a más de una familia.  

4. **Relación Cliente – Medicamento (Compra)**  
   - Toda compra debe registrar al menos **una unidad** de medicamento.  
   - La **fecha de compra** debe ser válida y no puede ser posterior a la fecha actual.  

5. **Restricciones sobre atributos numéricos**  
   - El número de **unidades en stock** y las **unidades vendidas** debe ser un valor **entero no negativo**.  
   - El **precio** de cada medicamento debe ser **mayor que cero**.  

6. **Relación Familia – Enfermedad**  
   - Una enfermedad debe estar asociada al menos a una familia de medicamentos que pueda tratarla.  
   - Una misma enfermedad puede estar vinculada a varias familias.  

---



