# DistribuidoraDespachoJava
Repositorio con proyecto Java de cálculo de despacho a domicilio, incluyendo documentación completa, instrucciones de Compilación y Ejecución, requerimientos e historias de usuario.

---
# 🚚 Distribuidora de Alimentos - Cálculo de Despacho

Este proyecto corresponde al desarrollo de una aplicación en **Java**, creada **sin utilizar un IDE**, únicamente con **Block de notas** de Windows y ejecutada mediante consola con el compilador `javac`.  
El sistema simula el proceso de compra en una **distribuidora de alimentos** que aplica reglas de negocio para el cálculo automático del despacho a domicilio, dependiendo del monto de la compra y la distancia recorrida.  

---

## 📌 Descripción General

La aplicación permite:  
- Registrar datos de un vehículo de despacho.  
- Capturar datos de una compra (total en pesos y distancia en kilómetros).  
- Calcular automáticamente el costo del envío según reglas de negocio.  
- Mostrar al usuario el detalle de la compra, costo de envío y total a pagar.  

---

## 🛠️ Instrucciones de Compilación y Ejecución

1. Abrir **Block de notas** en Windows.  
2. Copiar el código fuente del programa y guardarlo como:  Distribuidora.java
3. Abrir la **consola de comandos (CMD)** y ubicarse en la carpeta donde guardaste el archivo.  
4. Compilar el programa con la instruccion javac Distribuidora.java


## 4️⃣ Listado de Requerimientos

``
# Requerimientos Funcionales

1. Registrar datos del vehículo de despacho: marca, modelo, cilindrada, tipo de combustible y capacidad de pasajeros.
2. Ingresar total de compra y distancia en kilómetros entre centro y domicilio.
3. Calcular automáticamente el costo de despacho según reglas de negocio:
   - Compra ≥ 50.000 pesos: envío gratis si distancia ≤ 20 km
   - Compra entre 25.000 y 49.999 pesos: $150 por km
   - Compra < 25.000 pesos: $300 por km
4. Mostrar resultados completos: datos del vehículo, total de compra, costo de envío y total a pagar.
5. Interacción con el usuario mediante consola (entrada y salida estándar).

# Requerimientos No Funcionales

1. El programa debe ejecutarse en cualquier sistema operativo con JVM instalado.
2. El código debe ser legible, modular y documentado línea por línea.
3. La aplicación no utiliza IDE; se ejecuta desde un editor de texto simple y la línea de comandos.
4. El tiempo de respuesta del cálculo debe ser inmediato.



## 4️⃣ Historias de Usuario


# Historias de Usuario

## Historia 1
**Como** cliente de la distribuidora  
**Quiero** ingresar el total de mi compra y la distancia a mi domicilio  
**Para que** el sistema calcule automáticamente el costo de despacho y el total a pagar  

**Criterios de aceptación:**  
- El usuario ingresa valores válidos para la compra y la distancia.  
- Se muestra el costo de despacho según reglas de negocio.  
- Se muestra el total a pagar.

## Historia 2
**Como** encargado del centro de distribución  
**Quiero** registrar los datos del vehículo de despacho  
**Para que** quede registrado qué vehículo realiza la entrega  

**Criterios de aceptación:**  
- Se ingresan marca, modelo, cilindrada, tipo de combustible y capacidad de pasajeros.  
- Los datos se muestran correctamente al calcular el despacho.


  ## 📄 Explicación por grupos de líneas de Distribuidora.java

### 1️⃣ Importación de librerías
``
import java.util.Scanner;
```
-Se importa la clase Scanner del paquete java.util.
-Permite leer datos desde la entrada estándar (teclado).
-Es fundamental para capturar información ingresada por el usuario, como total de la compra, distancia o datos del vehículo.

```
### 2️⃣ Declaración de la clase principal

public class Distribuidora {
```

-Define la clase Distribuidora, que contiene toda la lógica del programa.
-public indica que la clase es accesible desde cualquier parte del proyecto.

```
3️⃣ Método principal

public static void main(String[] args) {
```
-Método que ejecuta el programa.
-static permite su ejecución sin crear un objeto de la clase.
-String[] args permite recibir argumentos desde la consola.

```
4️⃣ Creación del objeto Scanner

Scanner sc = new Scanner(System.in);
```
-Crea un objeto sc de la clase Scanner.
-Permite capturar datos ingresados por el usuario mediante consola.

```
5️⃣ Captura de datos del vehículo

String marca, modelo, cilindrada, tipoCombustible;
int capacidadPasajeros;

System.out.println("=== Registro del Vehículo de Despacho ===");
System.out.print("Ingrese la marca: ");
marca = sc.nextLine();
System.out.print("Ingrese el modelo: ");
modelo = sc.nextLine();
System.out.print("Ingrese la cilindrada: ");
cilindrada = sc.nextLine();
System.out.print("Ingrese el tipo de combustible: ");
tipoCombustible = sc.nextLine();
System.out.print("Ingrese la capacidad en pasajeros: ");
capacidadPasajeros = sc.nextInt();
```
-Se declaran variables para almacenar los datos del vehículo.
-System.out.print y System.out.println muestran mensajes en consola.
-sc.nextLine() captura texto; sc.nextInt() captura números enteros.

```
6️⃣ Captura de datos de la compra

double totalCompra, distanciaKm, costoEnvio = 0, totalPagar;

System.out.println("\n=== Compra del Cliente ===");
System.out.print("Ingrese el total de la compra en pesos: ");
totalCompra = sc.nextDouble();
System.out.print("Ingrese la distancia en km entre el centro X y su casa: ");
distanciaKm = sc.nextDouble();
```
-Se declaran variables double para valores con decimales.
-Captura el total de la compra y la distancia hasta el domicilio.

```
7️⃣ Cálculo del costo de despacho

if (totalCompra >= 50000 && distanciaKm <= 20) {
    costoEnvio = 0; // Envío gratis
} else if (totalCompra >= 25000 && totalCompra <= 49999) {
    costoEnvio = distanciaKm * 150;
} else if (totalCompra < 25000) {
    costoEnvio = distanciaKm * 300;
}
```
-Aplica las reglas de negocio según monto de compra y distancia.
-if y else if deciden la tarifa correcta.
-Se calcula el costo multiplicando los kilómetros por el precio correspondiente.

```
8️⃣ Cálculo del total a pagar

totalPagar = totalCompra + costoEnvio;
```
-Suma el total de la compra y el costo de envío para obtener el total final.

```
9️⃣ Mostrar resultados en consola

System.out.println("\n=== Detalle de la Compra y Despacho ===");
System.out.println("Vehículo de despacho: " + marca + " " + modelo + ", " + cilindrada + ", " + tipoCombustible);
System.out.println("Capacidad del vehículo: " + capacidadPasajeros + " pasajeros");
System.out.println("Total de la compra: $" + totalCompra);
System.out.println("Costo del envío: $" + costoEnvio);
System.out.println("TOTAL A PAGAR: $" + totalPagar);

sc.close();

```
-Muestra todos los datos ingresados y calculados en consola.
-sc.close() libera los recursos del objeto Scanner.
-Termina la ejecución del programa.




