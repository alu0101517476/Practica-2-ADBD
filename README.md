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


## 📑 Índice.




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

### 3.1. Relación Medicamento - Laboratorio.

### 3.2. Relación Medicamento - Familia.

### 3.3. Relación Medicamento - Cliente.

### 3.4. Relación Familia - Enfermedad.

### 3.5. Relación Medicamento - Tipo de medicamento

### 3.6. Relación Cliente - Tipo de cliente

--- 

