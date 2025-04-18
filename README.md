
# 1-CRIANDO O DICIONARIO DE ESTOQUE
estoque = {} #A gente está criando um dicionário vazio chamado estoque, que vai guardar todos os produtos da nossa loja.


# 2-MOSTAR O MENU NO TERMINAL
def mostrar_menu(): #Essa função só imprime no terminal as opções que o usuário pode escolher.
    print("\n" + "="*30)
    print("📦  CONTROLE DE ESTOQUE  📦".center(30))
    print("="*30)
    print('1️⃣ - Adicionar produto')
    print('2️⃣ - Remover produto')
    print('3️⃣ - Consultar estoque')
    print('4️⃣ - Atualizar quantidade')
    print('5️⃣ - Buscar produto')
    print('6️⃣ ❌ Sair')
    print("-"*30)

# 4-FUNÇÃO (adicionar produto)
def adicionar_produto():
    nome = str(input('Digite o nome do produto: ')).lower()
    if nome in estoque: #Verifica se o nome do produto já está no dicionário estoque
        print('Produto já existente. Atualize a quantidade se quiser.')
        return #Se já existir, avisa o usuário e não continua (por causa do return).
    quantidade = int(input('Quantidade: '))
    preco = float(input('Preço: '))
    estoque[nome] = {'quantidade': quantidade, 'preco': preco} #Cria uma nova entrada no dicionário estoque, com o nome do produto como chave, e outro dicionário como valor.
    print('Produto {} adicionado com sucesso ✅' .format(nome))

# 5-FUNÇÃO (remover_produto)
def remover_produto():
    nome = str(input('Nome do produto que deseja remover: ')).lower()
    if nome in estoque:
        del estoque[nome] #Se existir, usa del pra deletar a entrada inteira do produto no dicionário.
        print('Produto {} removido.' .format(nome))
    else:
        print('Produto não encontrado.')

# 6-Função consultar_estoque()
def consultar_estoque():
    if not estoque: #not estoque é o mesmo que dizer “estoque está vazio?” Se estiver, já mostra a mensagem e sai da função com return.
        print('Estoque vazio. ')
        return
    print("\n--- Estoque Atual ---")
    for nome, info in estoque.items():
        # Laço que percorre o dicionário estoque.
        # nome é a chave (nome do produto)
        # info é o valor, que é outro dicionário com quantidade e preço.
        print("{} - Qtd: {} - Preço: R${:.2f}".format(nome.title(), info["quantidade"], info["preco"]))
        # nome.title() deixa a primeira letra de cada palavra em maiúscula (ex: banana → Banana).

# 7-Função atualizar_quantidade()
def atualizar_estoque():
    nome = str(input('Nome do produto: ')).lower()
    if nome in estoque: #Verifica se o produto existe no dicionario estoque.
        nova_qtd = int(input('Digite a nova quantidade: ')) #Adiciona a nova quantidade 
        estoque[nome]["quantidade"] = nova_qtd #Adiciona o valor da quantidade no dicionario
        print('Quantidade de {} atulizada pra {}' .format(nome , nova_qtd))
    else:
        print('Produto não encontrado')

# 8. Função buscar_produto()
def buscar_produto():
    nome = str(input('Buscar produto pelo nome: '))
    if nome in estoque:
        #Verifica se o produto existe.
        info = estoque[nome] #Pega o dicionário com os dados do produto (quantidade e preço).
        print("{} - Qtd: {} - Preço: R${:.2f}" .format(nome.title(), info['quantidade'], info['preco']))
    else:
        print('Produto não encontrado')

# 3-LOOP PRINCIPAL DO PROGRAMA 
while True:
    mostrar_menu() # sem isso o menu não é mostrado na tela.
    opcao = int(input('Escolha uma opção: '))

    if opcao == 1:
        adicionar_produto()
    elif opcao == 2:
        remover_produto()
    elif opcao == 3:
        consultar_estoque()
    elif opcao == 4:
        atualizar_estoque()
    elif opcao == 5:
        buscar_produto()
    elif opcao == 6:
        print('Saindo...')
        break
    else:
        print('Opçao invalida. Tente novamente.')


