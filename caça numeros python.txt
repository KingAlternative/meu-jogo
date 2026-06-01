import random
import os

# ===  CAÇA-NÚMERO - JOGO SIMPLES DE ADIVINHAR ===
# Conceitos usados: variável, input, if/else, while, random, função

def limpar_tela():
    os.system('cls') # Limpa o terminal no Windows

def jogar():
    limpar_tela()
    print("=== CAÇA-NÚMERO ===")
    print("Tente adivinhar o número de 1 a 50!")
    
    # 1. Sorteia um número secreto entre 1 e 50
    numero_secreto = random.randint(1, 50)
    tentativas = 0
    acertou = False
    
    # 2. Loop principal do jogo
    while not acertou:
        try:
            # 3. Pede um chute pro jogador
            chute = int(input("\nSeu chute: "))
            tentativas += 1 # Aumenta 1 na contagem
            
            # 4. Compara o chute com o número secreto
            if chute < numero_secreto:
                print("MAIOR! Tenta um número mais alto ↑")
            elif chute > numero_secreto:
                print("MENOR! Tenta um número mais baixo ↓")
            else:
                # 5. Se acertou, sai do loop
                acertou = True
                limpar_tela()
                print(f"GANHOU! O número era {numero_secreto}!")
                print(f"Você precisou de {tentativas} tentativas.")
        
        except ValueError:
            # 6. Se o jogador digitar letra em vez de número
            print("ERRO: Digite só números!")

# 7. Loop pra jogar de novo
while True:
    jogar()
    jogar_novamente = input("\nJogar de novo? [S/N]: ").lower()
    if jogar_novamente != 's':
        print("Valeu por jogar! Caça numeros👻")
        break