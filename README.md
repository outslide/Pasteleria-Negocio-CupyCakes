# Pasteleria-Negocio-CupyCakes
Página web de negocio de pasteleria

# 🍰 Sistema de Gestión de Pastelería

Sistema web completo para gestión de pastelería con módulos de ventas, inventario, pedidos y análisis de datos. Incluye panel de administración con dashboard analítico y sistema de e-commerce para clientes.

## 📋 Descripción del Proyecto

Aplicación web desarrollada en PHP para la gestión integral de una pastelería que incluye:

- **E-commerce**: Catálogo de productos, carrito de compras, sistema de pedidos
- **Panel de Administración**: Dashboard con métricas de negocio, gestión de productos, pedidos, usuarios e inventario
- **Analytics**: Estadísticas de ventas, análisis de clientes, métricas de productos y reportes por distrito
- **Gestión de Pedidos**: Seguimiento de estados, métodos de pago, delivery/recojo
- **Sistema de Tickets**: Generación de comprobantes con código QR

## 🛠️ Requisitos del Sistema

### Software Requerido

- **PHP**: 7.4 o superior
- **MySQL/MariaDB**: 5.7 o superior
- **Servidor Web**: Apache (XAMPP recomendado)

### Extensiones PHP Necesarias

Las siguientes extensiones deben estar habilitadas en `php.ini`:

```ini
extension=gd         ; Para generación de imágenes y QR
extension=pdo_mysql  ; Para conexión a base de datos
extension=mbstring   ; Para manejo de caracteres multibyte
extension=openssl    ; Para funciones de seguridad
```

### Dependencias Externas

- **PHPQRCode**: Incluido en `phpqrcode/` (ya incluido en el proyecto)
- **Bootstrap 4**: CDN (cargado automáticamente)
- **Font Awesome**: CDN (cargado automáticamente)
- **jQuery**: CDN (cargado automáticamente)

## 📦 Instalación

### Paso 1: Clonar o Copiar el Proyecto

```bash
# Opción 1: Si tienes Git
git clone <url-del-repositorio>

# Opción 2: Copiar los archivos directamente
# Extraer el proyecto en: C:\xampp\htdocs\PASTELERIA NEGOCIO\
```

### Paso 2: Configurar la Base de Datos

1. **Iniciar XAMPP**: 
   - Abrir XAMPP Control Panel
   - Iniciar Apache y MySQL

2. **Crear la Base de Datos**:
   ```bash
   # Opción A: Desde línea de comandos
   C:\xampp\mysql\bin\mysql.exe -u root -e "CREATE DATABASE pasteleria CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
   
   # Opción B: Desde phpMyAdmin
   # Ir a http://localhost/phpmyadmin
   # Crear nueva base de datos llamada "pasteleria"
   ```

3. **Importar el Schema SQL**:
   ```bash
   # Opción A: Línea de comandos
   C:\xampp\mysql\bin\mysql.exe -u root pasteleria < "C:\xampp\htdocs\PASTELERIA NEGOCIO\cupycackes.sql"
   
   # Opción B: phpMyAdmin
   # Seleccionar base de datos "pasteleria"
   # Click en "Importar" → Seleccionar "cupycackes.sql" → Ejecutar
   ```

### Paso 3: Configurar Conexión a Base de Datos

Editar el archivo `db.php` si es necesario (valores por defecto):

```php
$host = 'localhost';
$db   = 'pasteleria';
$user = 'root';
$pass = '';  // Cambiar si tu MySQL tiene contraseña
$charset = 'utf8mb4';
```

### Paso 4: Configurar GD Extension (para QR)

Verificar que GD esté habilitado:

1. Abrir `C:\xampp\php\php.ini`
2. Buscar `;extension=gd`
3. Remover el `;` al inicio: `extension=gd`
4. Reiniciar Apache en XAMPP

### Paso 5: Permisos de Carpetas (Opcional)

Asegurar que las siguientes carpetas tengan permisos de escritura:
- `imagenes_productos/`
- `imagenes_categorias/`
- `comprobantes/` (si existe)

## 🚀 Ejecución del Proyecto

### Iniciar el Servidor

1. **Abrir XAMPP Control Panel**
2. **Iniciar servicios**:
   - Apache (puerto 80 por defecto)
   - MySQL (puerto 3306 por defecto)

### Acceder a la Aplicación

- **Página Principal (Cliente)**: http://localhost/PASTELERIA%20NEGOCIO/
- **Panel de Administración**: http://localhost/PASTELERIA%20NEGOCIO/admin.php
- **Login**: http://localhost/PASTELERIA%20NEGOCIO/login.php
- **Registro**: http://localhost/PASTELERIA%20NEGOCIO/registro.php

### Cambio de Puertos (Si es necesario)

Si el puerto 80 está ocupado:

1. En XAMPP Config → Apache (httpd.conf)
2. Cambiar `Listen 80` a `Listen 8080`
3. Acceder usando: `http://localhost:8080/PASTELERIA%20NEGOCIO/`

## 🔑 Credenciales de Prueba

### Usuario Administrador

```
Email: admin@pasteleria.com
Contraseña: admin123
Rol: admin
```

**Nota**: La contraseña debe estar hasheada en la BD. Si hay problemas de login, ejecutar:

```sql
UPDATE usuarios 
SET password = '$2y$10$O859SfJuCDWCOLtfmbgfv.wRMXmb6HgBBIluP4p0YYUTKabn6angq' 
WHERE email = 'admin@pasteleria.com';
```

### Usuario Cliente (Ejemplo)

```
Email: cliente@ejemplo.com
Contraseña: cliente123
Rol: cliente
```

**Crear nuevos usuarios** a través del formulario de registro o directamente en la BD.

## 📁 Estructura del Proyecto

```
PASTELERIA NEGOCIO/
├── admin.php              # Panel de administración
├── index.php              # Página principal/catálogo
├── login.php              # Sistema de autenticación
├── registro.php           # Registro de usuarios
├── carrito.php            # Carrito de compras
├── checkout.php           # Finalizar compra
├── ticket.php             # Generación de tickets
├── db.php                 # Configuración de BD
├── cupycackes.sql         # Schema de base de datos
├── includes/              # Componentes reutilizables
│   ├── header.php
│   ├── footer.php
│   ├── sidebar.php
│   └── navbar.php
├── css/                   # Estilos personalizados
├── js/                    # Scripts JavaScript
├── imagenes_productos/    # Imágenes de productos
├── phpqrcode/            # Librería para QR
└── README.md             # Este archivo
```

## 📊 Características del Dashboard

### Métricas Principales
- Total de pedidos, ingresos, usuarios y pedidos pendientes
- Ticket promedio
- Pedidos completados vs cancelados
- Margen de ganancia
- Costo total de delivery

### Analytics de Productos
- Productos más/menos vendidos
- Productos más recientes
- Stock por categoría
- Productos con mayores ingresos

### Analytics de Clientes
- Clientes por distrito
- Clientes nuevos vs recurrentes
- Clientes por rango de edad
- Top clientes por consumo anual

### Estadísticas de Ventas
- Ventas por día/semana/mes/año
- Ventas por categoría de producto
- Ventas por distrito
- Ventas por tipo de pago
- Ventas por estado del pedido
- Ventas por tipo de entrega
- Ventas por horas del día

## 🗄️ Esquema de Base de Datos

### Tablas Principales

**usuarios**
- Almacena clientes y administradores
- Campos: id, nombre, email, password, teléfono, edad, dirección, distrito, rol

**productos**
- Catálogo de productos
- Campos: id, nombre, descripción, precio, costo, stock, imagen, id_categoria, activo

**pedidos**
- Registro de pedidos
- Campos: id, id_usuario, fecha_pedido, total, costo_delivery, estado, metodo_pago, direccion_envio, distrito, tipo_entrega

**detalle_pedido**
- Items de cada pedido
- Campos: id, id_pedido, id_producto, cantidad, precio_unitario, subtotal

**categorias**
- Categorías de productos
- Campos: id, nombre, descripcion, imagen

**inventario**
- Control de insumos
- Campos: id, nombre, cantidad, unidad, precio_unitario

## 🔧 Troubleshooting

### Error: "Call to undefined function ImageCreate()"
**Solución**: Habilitar extensión GD en php.ini

### Error: "Access denied for user 'root'"
**Solución**: Verificar credenciales en db.php

### Imágenes no se muestran
**Solución**: Verificar permisos de carpeta `imagenes_productos/`

### Login no funciona
**Solución**: Verificar que la contraseña esté hasheada con `password_hash()`

### Puerto 80 ocupado
**Solución**: Cambiar puerto de Apache en XAMPP o usar puerto diferente

## 👨‍💻 Desarrollo

### Agregar Nuevos Productos

1. Login como admin
2. Ir a "Productos" en el menú lateral
3. Click en "+ Agregar Producto"
4. Llenar formulario y subir imagen

### Agregar Nuevas Categorías

1. Ir a sección de Productos
2. Gestionar categorías
3. Crear nueva categoría

### Ver Pedidos

1. Click en "Pedidos" en menú lateral
2. Ver lista de pedidos con filtros
3. Actualizar estado de pedidos

## 📝 Licencia

Este proyecto es de uso educativo/comercial.


**Versión**: 1.0  
**Última actualización**: Diciembre 2025
