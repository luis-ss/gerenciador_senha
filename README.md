# Password Manager
 
 An encrypted password manager made with python.

The manager needs access passwords.
Passwords are encrypted when saving and only decrypted after entering the access password

The application has an option to add a password; update a saved password or remove a password.

There is also the option to delete the account, resetting the application and deleting all saved information in the process.

#
# Functions:

# Function `criarConta()`

This function is called only on the user's first access or after the account has been deleted, so they can create the password for the manager's access. This function is very important for the security of the manager. To hide the password input in the terminal, the native Python library "getpass" was used. When the function is called, it asks the user to create a five-digit numeric password with a non-zero initial digit. After creating the password, it is used to encrypt the word "verificar" and save it in a verification file called "verificar.txt". Once these steps are completed, the code proceeds to the initial menu of the application.


# Function `excluirConta(primeiroAcesso=False)`

If the user forgets the access password or wants to delete their account, this function is called. If the user confirms the account deletion, the files "verificar.txt" and "senhas_salvas.txt" are opened and all their content is erased, thus removing all information from the manager. It receives a boolean parameter called "primeiroAcesso" to check if the account is being deleted from the manager's access menu, i.e., right after opening it, or if it is being deleted after accessing the account from the initial menu. This verification is done only to know where to continue in case the user wants to cancel the account deletion.


# Function `acessarConta(senha)`

After opening the manager and selecting the option to access the account, this function is called. It requires a parameter called "senha", which is the manager's access password. The entered password is verified by the function "verificarSenha()". If the password is correct, the code proceeds to the initial menu.


# Function `menuInicial()`

The initial menu provides the following options: "View saved passwords", "Add a new password", "Delete account", "EXIT".


# Function `verificarSenha()`

This function verifies the access password when entering the manager. It decrypts the text stored in the file "verificar.txt". If the password is verified as correct, access is granted; otherwise, an incorrect password message is displayed.


# Function `criptografarSenha(senha)`

The encryption is done by modifying the Unicode number of each password added by the user. The modification is done through calculations using the manager's access password. In other words, to decrypt it, the password is required, ensuring that only the account owner can access the passwords. The parameter requested by the function is the password to be encrypted, and once completed, it returns the fully encrypted password.


# Function `descriptografarSenha(key)`

The decryption is done through the reverse process of encryption. It receives the encrypted password as a parameter and returns the password in its original form, so that it can be viewed by the user or for verification. The parameter "key" is precisely the encrypted password.


# Function `mostrarSenhas()`

This function is used to display the list of saved passwords. The passwords are retrieved from the file "senhas_salvas.txt" and undergo a string processing, returning a list with the name and the decrypted password, allowing it to be viewed by the user. Each password is identified by an ID, so that it can be selected in the following functions. This function also displays a menu with the options: "Add password", "Update password", "Remove password", "Back to the initial menu", "EXIT".


# Function `removerSenha()`

This function is used to remove a saved password. When called, it asks for the ID of the password to be removed. This ID is used to remove the password from the list generated when calling the function "mostrarSenhas()". Once removed, the list is transformed into a string so that it can be saved again in the file of encrypted passwords.


# Function `atualizarSenha()`

The password update is done similarly to the removal. When called, it requires the ID of the password to be updated. The user is informed which password is being updated and asked for the new name and new password. The ID is used to find the password in the list of passwords, and the data is replaced. Then they are saved in the password file.


# Function `adicionarSenha()`

This function is responsible for saving a new password in the file of saved passwords. For this purpose, the "a" parameter of the open() function is used to open the file in "append" mode, i.e., a new string will be added. The password goes through the encryption process and is then saved.


# Function `tchau()`
When closing the program by choosing the "EXIT" option, the program ends and a goodbye message is displayed. The function "tchau()" is responsible for that.
