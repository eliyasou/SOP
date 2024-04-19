import random
import math
import time

# Funktion til at bestemme om et tilfældigt tal er et primtal
def er_primtal(tal):
    if tal < 2:
        return False
    for i in range(2, tal // 2 + 1):
        if tal % i == 0:
            return False
    return True

# Genererer et tilfældigt primtal mellem min_value og max_value
def generer_primtal(min_value, max_value):
    primtal = random.randint(min_value, max_value)
    while not er_primtal(primtal):
        primtal = random.randint(min_value, max_value)
    return primtal

# Funktion til at bestemme den private nøgle (d) vha. modulo
def mod_inverse(e, phi):
    for d in range(3, phi):
        if (d * e) % phi == 1:
            return d
    raise ValueError("Mod_inverse does not exist!")

# Genererer nøgler
def generer_nøgler():
    # Genererer primtal p og q
    p, q = generer_primtal(1000, 50000), generer_primtal(1000, 50000)
    while p == q:
        q = generer_primtal(1000, 50000)

    # Beregner n og phi(n)
    n = p * q
    phi_n = (p - 1) * (q - 1)

    # Genererer en tilfældig offentlig nøgle e
    e = random.randint(3, phi_n - 1)
    while math.gcd(e, phi_n) != 1:
        e = random.randint(3, phi_n - 1)

    # Genererer den private nøgle d
    d = mod_inverse(e, phi_n)

    # Printer nøgler
    print("Offentlig Nøgle (e, n):", e, n)
    print("Privat Nøgle (d, n):", d, n)

    return n, e, d

# Krypter funktion
def krypter(n, e):
    # Besked der skal krypteres
    besked = input("Skriv besked du vil kryptere: ")

    # Krypterer beskeden
    start_time=time.time()
    besked_ASCII = [ord(ka) for ka in besked]
    chiffertekst = [pow(ka, e, n) for ka in besked_ASCII]
    end_time=time.time()
    print("Besked krypteret i: ", chiffertekst)
    print("Krypteringstid: {:.6f} sekunder".format(end_time - start_time))
# Dekrypter funktion
def dekrypter(n, d):
    # Modtager chiffertekst fra brugeren
    chiffertekst = input("Indtast chiffertekst (adskilt med mellemrum): ").split()
    chiffertekst = [int(x) for x in chiffertekst]

    # Dekrypterer beskeden
    start_time = time.time()
    Afkode_msg = [pow(ka, d, n) for ka in chiffertekst]
    msg = "".join(chr(ka) for ka in Afkode_msg)
    end_time = time.time()

    print("Dekrypteret besked: ", msg)
    print("Dekrypteringstid: {:.6f} sekunder".format(end_time - start_time))
# Hovedfunktion
def main():
    start_time = time.time()
    # Genererer nøgler
    n, e, d = generer_nøgler()
    end_time = time.time()
    print("genering af nøgler: {:.6f} sekunder".format(end_time - start_time))
    while True:
        valg = input("Vil du kryptere eller dekryptere? (k/d): ").lower()
        if valg == 'k':
            krypter(n, e)
        elif valg == 'd':
            dekrypter(n, d)
        fortsæt = input("Vil du fortsætte? (ja/nej): ").lower()
        if fortsæt != 'ja':
            break

if __name__ == "__main__":
    main()
