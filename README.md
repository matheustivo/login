# login
Ettore auto-avaliacao

from os import system

def cadastrar(qtnd) -> None:
    with open('usuarios.txt', 'a') as file:
        for i in range(qtnd):
            user = input(f'Nome do usuário {i+1}: ')
            passwd = input(f'Senha do usuário {i+1}: ')
            file.write(f'{user}:{passwd}\n')

def login(user, passwd) -> bool:
    with open('usuarios.txt', 'r') as file:
        for row in file:
            if user in row:
                senha_user = str(row[row.index(':')+1:]).strip()
                if passwd == senha_user:
                    return True
        return False

def listar() -> None:
    with open('usuarios.txt', 'r') as file:
        print('--lista de usuarios--')
        print(file.read())
    input('aperte enter para continuar')

menu = """--Bem vindo--
[1] Cadastrar
[2] Login
[3] Listar
[4] Sair
Opção: """

if _name_ == '_main_':
    while True:
        system('cls')
        opcao = input(menu)
        system('cls')

        if opcao == '1':
            qtnd = int(input('Quantidade de usuários: '))
            cadastrar(qtnd)
        elif opcao == '2':
            user = input('Usuário: ')
            passwd = input('Senha: ')
            if login(user, passwd):
                print(f'Entrou com sucesso na conta {user}')
            else:
                print('Senha ou Usuário incorreto(s)')
                input('Pressione enter para continuar')
        elif opcao == '3':
            listar()
        elif opcao == '4':
            break
