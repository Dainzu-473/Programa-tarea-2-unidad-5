# Programa-tarea-2-unidad-5
def crear_sala():
    while True:
        try:
            filas = int(input("Numero de filas del cine: "))
            columnas = int(input("Numero de asientos por fila: "))
            if filas > 0 and columnas > 0:
                break
            else:
                print(" Deben de ser numeros mayores a 0.")
        except ValueError:
            print(" Ingresa valores validos.")

    sala = [["L" for _ in range(columnas)] for _ in range(filas)]
    print("\nSala creada exitosamente.\n")
    return sala



def mostrar_sala(sala):
    print("\n--- ESTADO DE LA SALA ---")
    for fila in sala:
        print(" ".join(fila))
    print()



def reservar_asiento(sala):
    try:
        f = int(input("Fila del asiento a reservar: ")) - 1
        c = int(input("Columna del asiento: ")) - 1
    except ValueError:
        print(" Ingresa valores validos.\n")
        return

    if f < 0 or f >= len(sala) or c < 0 or c >= len(sala[0]):
        print(" Ese asiento no existe.\n")
        return

    if sala[f][c] == "X":
        print(" Ese asiento ya esta ocupado.\n")
    else:
        sala[f][c] = "X"
        print(" Asiento reservado correctamente.\n")



def liberar_asiento(sala):
    try:
        f = int(input("Fila del asiento a liberar: ")) - 1
        c = int(input("Columna del asiento: ")) - 1
    except ValueError:
        print(" Ingresa valores validos.\n")
        return

    if f < 0 or f >= len(sala) or c < 0 or c >= len(sala[0]):
        print(" Ese asiento no existe.\n")
        return

    if sala[f][c] == "L":
        print(" Ese asiento ya esta libre.\n")
    else:
        sala[f][c] = "L"
        print(" Asiento liberado correctamente.\n")



def contar_asientos(sala):
    libres = sum(fila.count("L") for fila in sala)
    ocupados = sum(fila.count("X") for fila in sala)

    print("\n--- ESTADISTICAS ---")
    print(f"Asientos libres: {libres}")
    print(f"Asientos ocupados: {ocupados}\n")



def menu():
    sala = crear_sala()

    while True:
        print("======== MENU DEL CINE ========")
        print("1. Mostrar sala")
        print("2. Reservar asiento")
        print("3. Liberar asiento")
        print("4. Contar asientos")
        print("5. Salir")

        opcion = input("Elige una opcion: ")

        if opcion == "1":
            mostrar_sala(sala)
        elif opcion == "2":
            reservar_asiento(sala)
        elif opcion == "3":
            liberar_asiento(sala)
        elif opcion == "4":
            contar_asientos(sala)
        elif opcion == "5":
            print(" Saliendo del sistema de cine...")
            break
        else:
            print(" Opcion invalida.\n")


menu()
