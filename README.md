# Bautista-post1-u4
Actividad Post-Contenido 1 / Unidad 4

Se aplican principalmente los patrones:

- Chain of Responsibility (Cadena de Responsabilidad)
- Command (Comando)

Además, se incluye funcionalidad de deshacer (undo) y pruebas unitarias con JUnit 5.

---

## Tecnologías utilizadas

- Java 17
- Spring Boot 3
- Maven
- JUnit 5

---

## Estructura del proyecto


src/main/java/com/universidad/pedidos/
│
├── command/
│ ├── Comando.java
│ ├── ComandoConfirmar.java
│ ├── ComandoAplicarDescuento.java
│ └── HistorialComandos.java
│
├── cor/
│ ├── ValidadorPedido.java
│ ├── ValidadorStock.java
│ ├── ValidadorMonto.java
│ └── ValidadorCredito.java
│
├── modelo/
│ └── Pedido.java
│
└── PedidosApp.java


---

## Implementación de patrones

### Chain of Responsibility

Se utiliza para validar pedidos en múltiples etapas:

- Validación de stock
- Validación de monto mínimo
- Validación de crédito

Cada validador decide si continúa o detiene la cadena.

---

### Command

Se encapsulan acciones como objetos:

- Confirmar pedido
- Aplicar descuento

Permite ejecutar acciones y deshacerlas posteriormente.

---

### Undo (Historial de comandos)

Se implementa mediante una estructura tipo pila (Deque), permitiendo revertir la última acción ejecutada.

---

## Ejecución del proyecto

Compilar:


mvn clean package


Ejecutar:


mvn spring-boot:run


---

## Pruebas unitarias

Ejecutar pruebas:


mvn test


Resultados esperados:

- Todas las pruebas deben pasar correctamente
- Validación de pedidos
- Ejecución de comandos
- Funcionalidad de deshacer

---

## Ejemplo de salida


--- Validando pedido P-001 ---
[STOCK] OK: 3 unidades disponibles.
[MONTO] OK: total $45000.0 supera el mínimo.
[CREDITO] OK: crédito del cliente aprobado.
Resultado validación: true

[CMD] Pedido P-001 confirmado.
[CMD] Descuento 10% aplicado: $45000 → $40500

--- Deshaciendo última acción ---
[UNDO] Descuento revertido: $45000 restaurado


Evidencias

### Ejecución del sistema
<img width="1309" height="499" alt="image" src="https://github.com/user-attachments/assets/bfc37c1e-efa9-4d4f-bc7b-aed335b8ff86" />



### Pruebas unitarias
<img width="1266" height="479" alt="image" src="https://github.com/user-attachments/assets/dcdf5fa4-32c0-4d32-ad6d-fc63ab3a3b76" />


---

## Autor

Jahir Bautista
