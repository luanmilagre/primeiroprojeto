# primeiroprojeto
Meu primeiro jogo da forca em Python


import random

def escolher_palavra():
    return "baleia"

def mostrar_forca(palavra, letras_cocrretas):
    resultado = ""
    for letra in palavra:
        if letra in letras_corretas:
            resultado += letra + " "
        else:
            resultado += "_ "
    return resultado.strip()

def jogar_forca():
    palavra = escolher_palavra()
    letras_corretas = set()
    letras_erradas = set()
    tentativas_maximas = 6
    tentativas = 0

    print("Bem-vindo ao Jogo da Forca!")
    print("A palavra secreta tem", len(palavra), "letras.")

    while True:
        print("\n" + mostrar_forca(palavra, letras_corretas))
        print("Letras erradas:", " ".join(letras_erradas))
        print("Tentativas restantes:", tentativas_maximas - tentativas)

        if "_" not in mostrar_forca(palavra, letras_corretas):
            print("\nParabéns! Você acertou a palavra:", palavra)
            break

        if tentativas >= tentativas_maximas:
            print("\nVocê perdeu! A palavra secreta era:", palavra)
            break

        palpite = input("Digite uma letra: ").lower()

        if len(palpite) != 1 or not palpite.isalpha():
            print("Por favor, digite apenas uma letra válida.")
            continue

        if palpite in letras_corretas or palpite in letras_erradas:
            print("Você já tentou essa letra. Tente outra.")
            continue

        if palpite in palavra:
            letras_corretas.add(palpite)
        else:
            letras_erradas.add(palpite)
            tentativas += 1

if __name__ == "__main__":
    jogar_forca()
