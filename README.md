
---

# 🍽️ Sistema de Gestión de Restaurante — *Sabor Gourmet*

Aplicación web desarrollada con **Spring Boot 3.2.0**, diseñada para optimizar la gestión operativa de restaurantes.
Incluye módulos de pedidos, facturación, inventario, usuarios y auditoría, implementando **AOP** para el registro automático de acciones y **Spring Security** para autenticación y control de accesos.

---

## 🚀 Tecnologías Clave

* **Spring Boot 3.2.0** — Framework principal
* **Spring Data JPA + MySQL** — Persistencia de datos
* **Spring Security** — Control de autenticación y roles
* **AOP (Aspect-Oriented Programming)** — Auditoría automática
* **Thymeleaf + Bootstrap 5** — Interfaz web moderna y adaptable
* **BCrypt** — Cifrado de contraseñas

---

## ⚙️ Requisitos Previos

| Herramienta | Versión mínima                    |
| ----------- | --------------------------------- |
| Java        | 17                                |
| Maven       | 3.6                               |
| MySQL       | 8.0                               |
| IDE         | IntelliJ IDEA / Eclipse / VS Code |

---

## 🧩 Configuración Inicial

### 1️⃣ Crear base de datos

```sql
CREATE DATABASE sabor_gourmet CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 2️⃣ Editar credenciales en `application.properties`

```properties
spring.datasource.username=root
spring.datasource.password=tu_password
```

---

## ▶️ Ejecución del Proyecto

1. Clona o descarga el repositorio
2. Configura la conexión MySQL
3. Ejecuta el proyecto:

```bash
mvn spring-boot:run
```

O bien, desde tu IDE ejecuta la clase principal:

```java
SaborGourmetApplication.java
```

4. Accede en tu navegador a:
   👉 [http://localhost:8080](http://localhost:8080)

---

## 👥 Usuarios por Defecto

| Usuario  | Contraseña  | Rol      |
| -------- | ----------- | -------- |
| admin    | admin123    | ADMIN    |
| mozo     | mozo123     | MOZO     |
| cajero   | cajero123   | CAJERO   |
| cocinero | cocinero123 | COCINERO |

---

## 🧱 Estructura del Proyecto

```
src/main/java/pe/edu/uni/saborgourmet/
├── aspect/        → Auditoría AOP
├── config/        → Configuraciones (seguridad, inicialización)
├── controller/    → Controladores MVC
├── entity/        → Entidades JPA
├── repository/    → Repositorios de datos
└── service/       → Lógica de negocio

src/main/resources/
├── templates/     → Vistas Thymeleaf
└── application.properties
```

---

## 🔐 Roles y Permisos

| Rol          | Permisos principales                               |
| ------------ | -------------------------------------------------- |
| **ADMIN**    | Control total: usuarios, mesas, platos, inventario |
| **MOZO**     | Gestión de pedidos y mesas                         |
| **COCINERO** | Visualización y actualización de pedidos en cocina |
| **CAJERO**   | Ventas, facturación y pagos                        |

---

## 📦 Módulos del Sistema

### 🧑‍🤝‍🧑 Clientes y Mesas

* Registro de clientes
* Control del estado de mesas (disponible, ocupada, reservada)

### 🍽️ Menú y Platos

* Alta y edición de platos y bebidas
* Asociación de insumos y control de precios

### 🧾 Pedidos

* Registro, seguimiento y actualización de pedidos
* Estados: *pendiente*, *en preparación*, *servido*, *cerrado*

### 💵 Ventas y Facturación

* Facturas automáticas
* Pagos con efectivo, tarjeta o Yape

### 📦 Inventario

* Gestión y control de stock
* Alertas de insumos bajos

### 🛡️ Administración y Seguridad

* Gestión de usuarios y roles
* Bitácora de acciones con AOP

---

## 🕵️‍♂️ Auditoría con AOP

El sistema registra cada operación CRUD en la tabla `bitacora`, indicando:

* Usuario que ejecutó la acción
* Entidad afectada
* ID del registro
* Tipo de acción (CREAR, ACTUALIZAR, ELIMINAR)
* Fecha y hora

El componente `AuditoriaAspect` intercepta automáticamente los métodos de los servicios para mantener un historial completo.

---

## 🧰 Comandos Útiles

### Compilar:

```bash
mvn clean install
```

### Ejecutar pruebas:

```bash
mvn test
```

### Empaquetar (JAR):

```bash
mvn clean package
```

### Ejecutar en producción:

```bash
java -jar target/sabor-gourmet-1.0.0.jar
```

---

## ☁️ Despliegue

1. Ajusta las variables de entorno o `application.properties`
2. Actualiza las credenciales de la base de datos
3. Empaqueta con `mvn clean package`
4. Ejecuta el archivo `.jar` generado

---

## ⚠️ Notas Importantes

* Contraseñas cifradas con **BCrypt**
* Todas las acciones CRUD quedan registradas en la **bitácora**
* El acceso está protegido mediante **autenticación obligatoria**
* Cada **rol** controla las vistas y acciones disponibles

---

## 👨‍💻 Autor

Desarrollado para el curso **Desarrollo de Aplicaciones Web – Ciclo IV**
**Proyecto educativo — Uso no comercial**

---

