import random

# Lista con las opciones
opciones = ["Piedra", "Papel", "Tijera"]

# Diccionario con las reglas
reglas = {
    "Piedra": "Tijera",
    "Papel": "Piedra",
    "Tijera": "Papel"
}

# Función para jugar una ronda
def jugar_ronda():
    print("\nOpciones:")
    print("1 = Piedra")
    print("2 = Papel")
    print("3 = Tijera")

    eleccion = input("Elige una opción: ")

    if eleccion in ["1", "2", "3"]:
        jugador = opciones[int(eleccion) - 1]
    else:
        print("Opción no válida")
        return None

    computadora = random.choice(opciones)

    print("Jugador eligió:", jugador)
    print("Computadora eligió:", computadora)

    if jugador == computadora:
        return "Empate"

    elif reglas[jugador] == computadora:
        return "Jugador"

    else:
        return "Computadora"


# Ciclo principal para volver a jugar
while True:

    puntos_jugador = 0
    puntos_computadora = 0
    ronda = 1

    print("\n=== PIEDRA, PAPEL O TIJERA ===")
    print("Modo: Mejor de 5")

    while puntos_jugador < 3 and puntos_computadora < 3:

        print("\nRonda:", ronda)

        resultado = jugar_ronda()

        if resultado == "Jugador":
            print("Jugador gana la ronda")
            puntos_jugador += 1

        elif resultado == "Computadora":
            print("Computadora gana la ronda")
            puntos_computadora += 1

        elif resultado == "Empate":
            print("La ronda terminó en empate")

        print("Puntaje actual:")
        print("Jugador:", puntos_jugador)
        print("Computadora:", puntos_computadora)

        ronda += 1

    print("\n=== RESULTADO FINAL ===")

    if puntos_jugador == 3:
        print("🎉 El jugador gana el juego")
    else:
        print("💻 La computadora gana el juego")

    # Pregunta para volver a jugar
    respuesta = input("\n¿Quieres volver a jugar? (s/n): ")

    if respuesta.lower() != "s":
        print("Gracias por jugar 😊")
        break
