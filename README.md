# metodo_de_depreciacion
import math
## Método de linea recta

# Ejercicio 1: Depreciación anual de una computadora
def depreciacion_anual_computadora(C, S, n):
    D = (C - S) / n
    return D

C1 = 10000  # Costo de la computadora en soles
S1 = 1000   # Valor de desecho
n1 = 3      # Vida útil en años

depreciacion_computadora = depreciacion_anual_computadora(C1, S1, n1)
print(f"La depreciación anual de la computadora es de S/.{depreciacion_computadora:.2f}")

# Ejercicio 2: Depreciación total y por unidad producida de una máquina de chocolate
def depreciacion_por_unidad(C, S, n):
    D_total = C - S
    D_unidad = D_total / n
    return D_total, D_unidad

C2 = 118500   # Costo de la máquina en dólares
S2 = C2 * 0.15  # Valor de salvamento (15% del costo)
n2 = 10000000   # Total de unidades (barras de chocolate)

depreciacion_total, depreciacion_unidad = depreciacion_por_unidad(C2, S2, n2)
print(f"La depreciación total es de S/.{depreciacion_total:.2f} y la depreciación por unidad es de S/.{depreciacion_unidad:.7f}")

# Ejercicio 3: Depreciación anual de un activo
def depreciacion_anual_activo(C, S, n):
    D = (C - S) / n
    return D

C3 = 80000   # Costo del activo en soles
S3 = 15000   # Valor de salvamento
n3 = 5       # Vida útil en años

depreciacion_activo = depreciacion_anual_activo(C3, S3, n3)
print(f"La depreciación anual del activo es de S/.{depreciacion_activo:.2f}")

# Ejercicio 4: Depreciación anual de una motocicleta
def depreciacion_anual_moto(C, S, n):
    D = (C - S) / n
    return D

C4 = 41000   # Costo de la motocicleta en soles
S4 = 1000    # Valor residual
n4 = 5       # Vida útil en años

depreciacion_moto = depreciacion_anual_moto(C4, S4, n4)
print(f"La depreciación anual de la motocicleta es de S/.{depreciacion_moto:.2f}")

## Método de porcentaje fijo

# Ejercicio 1: Tasa de depreciación para un gato hidráulico
def tasa_depreciacion_gato(C, S, n):
    # Cálculo de la tasa de depreciación utilizando logaritmos
    d = 1 - (S / C)**(1 / n)
    return d * 100  # Convertimos la tasa a porcentaje

C1 = 25000   # Costo del gato hidráulico
S1 = 6000    # Valor de salvamento
n1 = 7       # Vida útil en años

tasa_gato = tasa_depreciacion_gato(C1, S1, n1)
print(f"La tasa de depreciación anual del gato hidráulico es de {tasa_gato:.4f}%")

# Ejercicio 2: Tasa de depreciación y tabla de depreciación para una máquina industrial
def tasa_depreciacion_maquina(C, S, n):
    # Cálculo de la tasa de depreciación utilizando logaritmos
    d = 1 - (S / C)**(1 / n)
    return d * 100  # Convertimos la tasa a porcentaje

def tabla_depreciacion(C, S, d, n):
    # Genera una tabla de depreciación año por año
    tabla = []
    valor_libro = C
    for i in range(1, n + 1):
        depreciacion_anual = valor_libro * d
        valor_libro -= depreciacion_anual
        tabla.append((i, depreciacion_anual, valor_libro))
    return tabla

C2 = 80000     # Costo de la máquina industrial
S2 = 10000     # Valor de salvamento
n2 = 8         # Vida útil en años

# Calculamos la tasa de depreciación
tasa_maquina = tasa_depreciacion_maquina(C2, S2, n2) / 100  # Convertimos a decimal para la tabla
print(f"La tasa de depreciación anual de la máquina industrial es de {tasa_maquina * 100:.2f}%")

# Generamos la tabla de depreciación
tabla = tabla_depreciacion(C2, S2, tasa_maquina, n2)

# Imprimimos la tabla de depreciación
print("Año\tDepreciación Anual\tValor en Libros")
for año, depreciacion_anual, valor_libro in tabla:
    print(f"{año}\t${depreciacion_anual:.2f}\t\t\t${valor_libro:.2f}")
    # Ejercicio 3: Cálculo del valor de salvamento de una computadora después de 5 años
def valor_salvamento(C, d, n):
    # Calcula el valor de salvamento
    S = C * (1 - d)**n
    return S

# Datos del ejercicio 3
C3 = 30000   # Costo inicial de la computadora
d3 = 0.15    # Tasa de depreciación anual
n3 = 5       # Vida útil en años

# Calculamos el valor de salvamento
valor_salvamento_computadora = valor_salvamento(C3, d3, n3)
print(f"El valor de salvamento al final de {n3} años será de ${valor_salvamento_computadora:.2f}")

# Ejercicio 4: Cálculo del costo original de una máquina con un valor de salvamento conocido
def costo_original(S, d, n):
    # Calcula el costo original usando el valor de salvamento
    C = S / (1 - d)**n
    return C

# Datos del ejercicio 4
S4 = 5000    # Valor de salvamento de la máquina
d4 = 0.10    # Tasa de depreciación anual
n4 = 10      # Vida útil en años

# Calculamos el costo original
costo_original_maquina = costo_original(S4, d4, n4)
print(f"El costo original de la máquina fue de aproximadamente ${costo_original_maquina:.2f}")

## Método de suma de dígitos

# Función para calcular depreciación anual usando el método de suma de dígitos
def depreciacion_suma_digitos(costo_inicial, valor_rescate, vida_util):
    suma_digitos = sum(range(1, vida_util + 1))
    valor_depreciable = costo_inicial - valor_rescate
    depreciaciones = []

    # Cálculo de la depreciación para cada año
    for year in range(vida_util, 0, -1):
        fraccion = year / suma_digitos
        depreciacion_anual = fraccion * valor_depreciable
        depreciaciones.append(depreciacion_anual)
    
    # Crear la tabla de depreciación
    depreciacion_acumulada = 0
    valor_neto = costo_inicial
    tabla = []

    for i, d in enumerate(depreciaciones, start=1):
        depreciacion_acumulada += d
        valor_neto -= d
        tabla.append({
            "Año": i,
            "Depreciación Anual": round(d, 2),
            "Depreciación Acumulada": round(depreciacion_acumulada, 2),
            "Valor Neto": round(valor_neto, 2)
        })
    return tabla

# Ejercicio 1
print("Ejercicio 1 - Equipo de Computación")
tabla1 = depreciacion_suma_digitos(6500, 500, 5)
for row in tabla1:
    print(row)

# Ejercicio 2
print("\nEjercicio 2 - Tractor")
tabla2 = depreciacion_suma_digitos(640000, 115200, 6)
for row in tabla2:
    print(row)

# Ejercicio 3
print("\nEjercicio 3 - Máquina")
tabla3 = depreciacion_suma_digitos(20000, 0, 5)
for row in tabla3:
    print(row)

# Ejercicio 4
print("\nEjercicio 4 - Computadora")
tabla4 = depreciacion_suma_digitos(10000, 1000, 4)
for row in tabla4:
    print(row)
