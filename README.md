# turbo-octo-potato
import tkinter as tk
from tkinter import messagebox

# Função para verificar as credenciais
def verificar_login():
    # Credenciais de exemplo
    RA_esperado = "123456789"
    senha_esperada = "senha123"

    # Obtendo os valores dos campos de entrada
    RA_digitado = entrada_RA.get()
    senha_digitada = entrada_senha.get()

    # Verificando se o RA e a senha estão corretos
    if RA_digitado == RA_esperado and senha_digitada == senha_esperada:
        messagebox.showinfo("Login bem-sucedido", "Você entrou com sucesso no aplicativo!")
        # Aqui você pode redirecionar para o próximo passo do seu aplicativo, por exemplo:
        # abrir_arbore_de_leitura()
    else:
        messagebox.showerror("Erro", "RA ou senha incorretos, tente novamente.")

# Criando a janela principal
root = tk.Tk()
root.title("Login - Árvore de Leitura")

# Tamanho da janela
root.geometry("400x300")

# Labels e entradas para RA e senha
label_RA = tk.Label(root, text="RA Escolar:")
label_RA.pack(pady=10)

entrada_RA = tk.Entry(root)
entrada_RA.pack(pady=5)

label_senha = tk.Label(root, text="Senha:")
label_senha.pack(pady=10)

entrada_senha = tk.Entry(root, show="*")
entrada_senha.pack(pady=5)

# Botão de login
botao_login = tk.Button(root, text="Entrar", command=verificar_login)
botao_login.pack(pady=20)

# Iniciar o loop da interface gráfica
root.mainloop()
