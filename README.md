# playlist_festival.py

nombres, artistas, duraciones, popularidades = [], [], [], []


def agregar():
    for _ in range(int(input("¿Cuántas canciones?: "))):
        nombres.append(input("Nombre: "))
        artistas.append(input("Artista: "))
        duraciones.append(float(input("Duración (min): ")))
        popularidades.append(int(input("Popularidad (1-100): ")))


def reportes():
    if not nombres: return print("Sin canciones.")
    prom = sum(popularidades) / len(popularidades)
    mx, mn = popularidades.index(max(popularidades)), popularidades.index(min(popularidades))
    print(f"\nTotal: {len(nombres)} | Duración: {sum(duraciones):.2f} min | Promedio: {prom:.2f}")
    print(f"Más popular: {nombres[mx]} ({popularidades[mx]}) | Menos popular: {nombres[mn]} ({popularidades[mn]})")


def buscar():
    if not nombres: return print("Sin canciones.")
    op = input("1. Artista  2. Rango popularidad: ")
    if op == "1":
        a = input("Artista: ").lower()
        for i in range(len(nombres)):
            if a in artistas[i].lower(): print(f"{nombres[i]} - {artistas[i]} ({popularidades[i]})")
    elif op == "2":
        lo, hi = int(input("Mín: ")), int(input("Máx: "))
        for i in range(len(nombres)):
            if lo <= popularidades[i] <= hi: print(f"{nombres[i]} - {artistas[i]} ({popularidades[i]})")


def recomendada():
    if not nombres: return print("Sin canciones.")
    prom = sum(popularidades) / len(popularidades)
    print(f"\n--- Recomendada (> {prom:.2f}) ---")
    for i in range(len(nombres)):
        if popularidades[i] > prom: print(f"{nombres[i]} - {artistas[i]} ({popularidades[i]})")


def menu():
    while True:
        op = input("\n1.Agregar 2.Reportes 3.Buscar 4.Recomendada 5.Salir: ")
        if op == "1": agregar()
        elif op == "2": reportes()
        elif op == "3": buscar()
        elif op == "4": recomendada()
        elif op == "5": break


menu()
