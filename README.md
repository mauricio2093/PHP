# 🐘 Guía Definitiva para Aprender PHP – Desde Cero hasta Avanzado

Bienvenido a esta guía de aprendizaje progresivo de **PHP**. Aprenderás desde los fundamentos hasta patrones avanzados, con ejemplos reales, buenas prácticas modernas y enlaces útiles.

>  Ideal para desarrolladores web, estudiantes autodidactas o freelancers que quieran dominar PHP profesionalmente.

---

##  Índice de Contenidos

1. [Introducción a PHP y entorno de desarrollo](#1-introducción-a-php-y-entorno-de-desarrollo)
2. [Variables, tipos y operadores](#2-variables-tipos-y-operadores)
3. [Estructuras de control](#3-estructuras-de-control)
4. [Funciones](#4-funciones)
5. [Arrays](#5-arrays)
6. [Formularios y métodos HTTP](#6-formularios-y-métodos-http)
7. [Superglobales y sesiones](#7-superglobales-y-sesiones)
8. [Programación Orientada a Objetos (POO)](#8-poo-programación-orientada-a-objetos)
9. [Archivos y rutas](#9-archivos-y-rutas)
10. [Bases de datos MySQL](#10-bases-de-datos-mysql)
11. [Errores y excepciones](#11-errores-y-excepciones)
12. [Buenas prácticas](#12-buenas-prácticas)
13. [PHP moderno: Composer y Autoloading](#13-php-moderno-composer-y-autoloading)
14. [Seguridad básica en PHP](#14-seguridad-básica-en-php)
15. [Introducción a frameworks: Laravel](#15-frameworks-laravel-intro)
16. [Recursos adicionales y documentación](#16-recursos-útiles)

---

##  1. Introducción a PHP y entorno de desarrollo

**PHP** es un lenguaje de programación del lado del servidor, muy usado en desarrollo web.

###  Documentación:
  - Sitio oficial: [https://www.php.net](https://www.php.net)
  - Documentación en español: [Manual de PHP](https://www.php.net/manual/es/)

### Requisitos
- Tener PHP instalado localmente (usa `php -v` para verificar)
- Servidor local como [XAMPP](https://www.apachefriends.org/es/index.html), [Laragon](https://laragon.org/) o usar `php -S localhost:8000`

```php
<?php
echo "Hola, Mundo!";
```
## 🧠 PHP es de tipado dinámico, débil y gradual
### Conceptos clave
- Tipado **dinámico**: PHP infiere el tipo en tiempo de ejecución
- Tipado **débil**: convierte tipos automáticamente (aunque puede ser impredecible)
- Tipado **gradual** (desde PHP 7): puedes declarar tipos

```php
// Tipado débil
echo "5" + 2; // Devuelve 7

// Tipado gradual
declare(strict_types=1);
function sumar(int $a, int $b): int {
  return $a + $b;
}
```


---

##  2. Variables, tipos y operadores
Permiten tomar decisiones o repetir bloques de código.

```php
$nombre = "Mauricio";
$edad = 30;
$activo = true;
```
###  Tipos soportados:
 `string`, `int`, `float`, `bool`, `array`, `object`, `null`

###  Operadores comunes:
  - Aritméticos: `+`, `-`, `*`, `/`, `%`
  - Comparación: `==`, `===`, `!=`, `!==`, `<`, `>`
  - Lógicos: `&&`, `||`, `!`

###  Recursos:
  - [Tipos en PHP (inglés)](https://www.php.net/manual/en/language.types.php) 
  - [Operadores en PHP (español)](https://www.php.net/manual/es/language.operators.php)

---

##  3. Estructuras de control

```php
if ($edad >= 18) {
    echo "Eres mayor de edad.";
} elseif ($edad > 0) {
    echo "Eres menor de edad.";
} else {
    echo "Edad inválida.";
}
```
###  Bucles:
  - Condicionales: `if`, `else`, `switch`
  - Bucles: `for`, `while`, `foreach`

###  Más información:
  - [Estructuras de control en PHP (español)](https://www.php.net/manual/es/control-structures.php)

---

##  4. Funciones
Bloques reutilizables de código que pueden recibir parámetros y devolver valores.

###  Ejemplo:
```php
function saludar($nombre = "invitado") {
  return "Hola, $nombre";
}
```

```php
$fn = function() {
  return "Hola";
};
```
###  Características:
  -Valores por defecto
  -Scope (`global`,`static`)
  -Funciones anónima

###  Documentación:
  - [Funciones PHP (inglés)](https://www.php.net/manual/en/functions.user-defined.php)

---

##  5. Arrays
Estructuras que permiten almacenar múltiples valores.

```php
$frutas = ["manzana", "pera", "uva"];
echo $frutas[1]; // pera
```

###  Funciones útiles:

  - Arrays indexados y asociativos
  - Funciones: `array_map()`, `array_filter()`, `count()`, `array_push()`

###  Referencia:
  - [Trabajar con arrays (español)](https://www.php.net/manual/es/language.types.array.php)

---

##  6. Formularios y métodos HTTP

PHP permite procesar datos de formularios mediante las superglobales.

```html
<form method="POST">
  <input type="text" name="nombre" />
</form>
```

```php
$nombre = $_POST["nombre"] ?? "Desconocido";
```

###  Superglobales
  - `$_GET`, `$_POST`, `$_REQUEST`
  - Validación básica

###  Info:

  - [Formularios en PHP (español)](https://www.php.net/manual/es/tutorial.forms.php)

---

##  7. Superglobales y sesiones

Acceso global a datos del servidor, cliente y sesión.

###  Ejemplo:
```php
session_start();
$_SESSION['usuario'] = "mauricio";
```
###  Otras superglobales:
  - Variables: `$_SESSION`, `$_COOKIE`, `$_SERVER`, `$_FILES`, `$_ENV`

###  Documentación:
  - [Superglobales (español)](https://www.php.net/manual/es/language.variables.superglobals.php)

---

##  8. POO (Programación Orientada a Objetos)
Facilita la creación de estructuras reutilizables y escalables.

###  Ejemplo:
```php
class Persona {
  public $nombre;
  function __construct($nombre) {
    $this->nombre = $nombre;
  }
}
```
###  Conceptos clave:
  - Clases, objetos, herencia, interfaces, traits. 
  - Encapsulamiento(`public`, `private`, `protected`)

###  Recursos:
  - [POO en PHP (español)](https://www.php.net/manual/es/language.oop5.php)

---

##  9. Archivos y rutas
PHP ofrece funciones nativas para trabajar con archivos.
```php
file_put_contents("log.txt", "Registro");
$content = file_get_contents("log.txt");
```
###  Funciones útiles:
  - `fopen()`, `fwrite()`, `file_exists()`, `unlink()`

###  Más info
  - [Manejo de archivos (español)](https://www.php.net/manual/es/book.filesystem.php)

---

##  10. Bases de datos MySQL
PHP puede conectarse a bases de datos usando extensiones como `mysqli` o `PDO`.
### mysqli:
```php
$conn = new mysqli("localhost", "root", "", "mi_bd");
```

### PDO (recomendado):
```php
$db = new PDO("mysql:host=localhost;dbname=mi_bd", "root", "");
```
###  Consultas seguras:
  - Consultas preparadas, `fetch()`, `bindParam()`

###  Documentación:
  - [MySQLi (español)](https://www.php.net/manual/es/book.mysqli.php) 
  - [PDO (español)](https://www.php.net/manual/es/book.pdo.php)

---

##  11. Errores y excepciones
Gestiona errores y excepciones de forma controlada.
```php
try {
  throw new Exception("Ocurrió un error");
} catch (Exception $e) {
  echo $e->getMessage();
}
```
###  Tipos de errores:
  - `E_ERROR`, `E_WARNING`, `E_NOTICE`

###  Info:
  - [Manejo de errores PHP (español)](https://www.php.net/manual/es/ref.errorfunc.php)

---

##  12. Buenas prácticas
Escribe código mantenible y escalable.
###  Recomendaciones:
  - Nombres descriptivos
  - Separar lógica y presentación (MVC)
  - Validar todos los inputs
  - No repetir código (DRY)
###  Más:
  - [PHP: The Right Way](https://phptherightway.com/) 
  - [Guías de estilo PSR (PHP-FIG)](https://www.php-fig.org/psr/)

---

##  13. PHP moderno: Composer y Autoloading

```bash
composer init
composer require monolog/monolog
```
🔧 Ejemplo:
```php
declare(strict_types=1);
function sumar(int $a, int $b): int {
  return $a + $b;
}
```
###  Uso de Composer:
```bash
composer init
composer require monolog/monolog
}
```
###  Autoload PSR-4:
  - PSR-4 Autoload, Namespaces, Composer.json

###  Recursos:
  - [Composer Docs (inglés)](https://getcomposer.org/doc/) 
  - [PSR-4](https://www.php-fig.org/psr/psr-4/)
  - [PHP-Moderno](https://desarrolloweb.com/manuales/manual-php.html)
---

##  14. Seguridad básica en PHP

Protege tus aplicaciones contra amenazas comunes.

###  Prácticas recomendadas:
  - `htmlspecialchars()` o `filter_input()` para sanitizar entradas
  - `password_hash()` y `password_verify()` para contraseñas
  - Proteger sesiones: usar `session_regenerate_id()`
  - Validación estricta y control de sesiones

###  Guías:
  - [OWASP PHP Security Project](https://owasp.org/www-project-secure-php-development/) 
  - [Seguridad en PHP (español)](https://www.php.net/manual/es/security.php)

---

##  15. Frameworks – Laravel (Intro)

```bash
composer create-project laravel/laravel nombre-proyecto
```
###  Conceptos básicos:
  - Rutas (`web.php`), controladores, Blade, migraciones, Eloquent ORM

###  Documentación:
  - [Documentación Laravel (español)](https://laravel.com/docs/11.x)

---

##  16. Recursos útiles

  - [PHP.net](https://www.php.net/)
  - [Manual en español](https://www.php.net/manual/es/)
  - [Laravel Docs (ES)](https://laravel.com/docs/11.x)
  - [DesarrolloWeb.net](https://desarrolloweb.com/)
  - [PHP: The Right Way](https://phptherightway.com/)

---

## 🔹 Bonus Hacks 

```php
var_dump(); // Debug detallado
print_r();   // Debug simple
dd();        // Laravel dump & die
```

```php
get_defined_vars(); // Variables en el contexto
$_SERVER['REQUEST_URI']; // Ruta actual
```

---

