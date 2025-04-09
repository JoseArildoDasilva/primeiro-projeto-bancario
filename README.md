menu = """" 

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """
saldo = 0
equilibrio = 0 
limite=500 
extrato = "" 
numero_saques = 0
LIMITE_SAQUES =3

while True:

    opcao =input (menu)

    if opcao == "d":
        valor = float(input("Informo o valor do depósito:"))
        
        if valor > 0:
            saldo += valor 
            extrato += f"Depósito: R$ {valor:.2f}\n" 
           
        else:
            print("Operção falhou! o valor é invalido.")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        execedeu_limite = valor > limite
        
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
             print("Operaçõa falhou! você não tem saldo suficiente") 

        elif execedeu_limite:
              print(" Operação falhou o valor do saque excede o limite") 
        
        elif excedeu_saques:
              print(" Operação falhou Número máximo de saques excedido.")

        elif valor > 0:
             saldo -= valor
             extrato += f"saque: R$ {valor:2f}\n"
             numero_saques +=1     

        else:
            print ("Operação falhou! o valor informado é  inválido.") 

    elif opcao == "e":
        print("\n================= EXTRATO =================")
        print("Não foram realiszadas movimentções." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("===============================================")
    
    elif opcao == "q":
        break     

    else:
        print("Operação Invalida, por favor selecione novamente a operação desejada.")
