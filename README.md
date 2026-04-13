# Bautista-post1-u4
Actividad Post-Contenido 1 / Unidad 4

Sistema de Pedidos - Patrones de Comportamiento
Descripción

Este proyecto implementa un sistema de gestión de pedidos aplicando diferentes patrones de diseño de comportamiento en Java. El objetivo es demostrar cómo desacoplar la lógica de negocio mediante estrategias reutilizables, permitiendo modificar el comportamiento del sistema en tiempo de ejecución.

Se implementa principalmente el patrón Strategy para gestionar descuentos dinámicos sobre un carrito de compras.

Tecnologías utilizadas
Java 17
Maven
JUnit 5
Spring (anotaciones básicas)
Estructura del proyecto
src/
 ├── main/
 │    └── java/
 │         └── com/universidad/pedidos/
 │              ├── cor/
 │              ├── modelo/
 │              ├── observer/
 │              └── strategy/
 │
 └── test/
      └── java/
           └── com/universidad/pedidos/
Patrón Strategy

El patrón Strategy permite definir una familia de algoritmos (en este caso, descuentos), encapsularlos y hacerlos intercambiables en tiempo de ejecución sin modificar el código cliente.

Interfaz principal
public interface EstrategiaDescuento {
    double calcular(double subtotal);
    String getNombre();
}
Implementaciones de estrategias
Descuento por temporada

Aplica un 20% de descuento sobre el subtotal.

public class DescuentoTemporada implements EstrategiaDescuento {
    public double calcular(double subtotal) {
        return subtotal * 0.20;
    }
}
Descuento VIP

Aplica un 30% de descuento.

public class DescuentoVIP implements EstrategiaDescuento {
    public double calcular(double subtotal) {
        return subtotal * 0.30;
    }
}
Descuento por cupón

Aplica un descuento fijo de hasta 15.000.

public class DescuentoCupon implements EstrategiaDescuento {
    public double calcular(double subtotal) {
        return Math.min(subtotal, 15000);
    }
}
Servicio principal

El CarritoService administra las estrategias disponibles y permite activar una en tiempo de ejecución.

public class CarritoService {

    private final List<EstrategiaDescuento> estrategiasDisponibles;
    private EstrategiaDescuento estrategiaActiva;

    public void activarDescuento(String nombre) { ... }

    public double calcularTotal(double subtotal) { ... }
}
Ejecución de pruebas

Para ejecutar todos los tests:

mvn clean test

Para ejecutar solo las pruebas del patrón Strategy:

mvn -Dtest=StrategyTests test
Pruebas implementadas

Se validan los siguientes casos:

Aplicación correcta del descuento de temporada (20%)
Aplicación correcta del descuento VIP (30%)
Aplicación del cupón fijo
Cambio de estrategia en tiempo de ejecución
Manejo de estrategia inválida mediante excepción
Ejemplo de salida
[CARRITO] Estrategia activada: Temporada (20%)
[CARRITO] Temporada (20%) -> Descuento: $20000.00 | Total: $80000.00


Evidencias

### Ejecución del sistema
<img width="1894" height="982" alt="image" src="https://github.com/user-attachments/assets/422e61aa-dd0a-4368-8f5f-1929cb3a3490" />


---

## Autor

Jahir Bautista
