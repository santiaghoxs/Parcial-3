# Parcial-3
repositorio parcial 3 programacion de computadores
class Producto:
    def __init__(self, nombre, precio, stock):
        self.nombre = nombre
        self.precio = precio
        self.__stock = stock  # Atributo privado

    def vender(self, cantidad):
        if cantidad <= self.__stock:
            self.__stock -= cantidad
            print(f"Venta exitosa: {cantidad} unidades de {self.nombre}")
        else:
            print("Stock insuficiente")

    def reabastecer(self, cantidad):
        self.__stock += cantidad
        print(f"Reabastecimiento exitoso: {cantidad} unidades de {self.nombre}")

    def mostrar_info(self):
        return f"{self.nombre} - Precio: ${self.precio}, Stock: {self.__stock}"

class Inventario:
    def __init__(self):
        self.productos = []

    def agregar_producto(self, producto):
        self.productos.append(producto)
        print(f"Producto agregado: {producto.nombre}")

    def eliminar_producto(self, nombre):
        self.productos = [p for p in self.productos if p.nombre != nombre]
        print(f"Producto eliminado: {nombre}")

    def mostrar_inventario(self):
        print("\n--- Inventario de la Tienda ---")
        for producto in self.productos:
            print(producto.mostrar_info())

# Uso del sistema
inventario = Inventario()

# Agregar productos
silla1 = Producto("Silla Ejecutiva", 150, 10)
silla2 = Producto("Silla Gamer", 200, 5)

inventario.agregar_producto(silla1)
inventario.agregar_producto(silla2)

# Mostrar inventario
inventario.mostrar_inventario()

# Vender y reabastecer
silla1.vender(2)
silla2.reabastecer(3)

# Mostrar inventario actualizado
inventario.mostrar_inventario()

# Eliminar un producto
inventario.eliminar_producto("Silla Gamer")

# Mostrar inventario final
inventario.mostrar_inventario()
