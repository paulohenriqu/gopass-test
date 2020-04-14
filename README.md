## Gopass Test
## Installation
gopass is a simple but powerful password manager for your terminal.
Each secret lives inside of a `gpg` encrypted file and it has a great integration with git and easier management of recipients
https://www.gopass.pw/#install
## Clone Store

    gopass clone https://github.com/paulohenriqu/gopass-test.git COMPE --sync gitcli


## Add Account

    gopass insert COMPE/{Bank Code}/{PF/PJ}/{YourName} -m
Example:

    gopass insert COMPE/033/PF/name -m

This command will open your text editor, use this template to input the account details:

```
Banco / Tipo de Conta
  Operador: <CPF / Usuário>
  Senha: <A senha>
  Agencia: <Agência>
  Conta: <Conta>

  Dono: <Nome do dono>
```

When you exit the editor and save, the file will be encrypted and the content will be uploaded to the remote repository.

## Show Account Details
To list all the accounts in the store you can use the following command:

    gopass ls
To see the decrypted deatails of an account use this command:

    gopass show COMPE/033/PF/name
## Add Recipients
If you want to add a teammate GPG key, so they can read the files, you have to:

 - Have them upload the public key to a key server. Ex.: https://keyserver.ubuntu.com
 - Add the public GPG key to your key ring:


    gpg --keyserver keyserver.ubuntu.com --recv-keys {KEY_ID}

	Ex:

    gpg --keyserver keyserver.ubuntu.com --recv-keys 04CE38DA9A9E0A3F

 - Add the key to the gopass store:
	

    gopass recipients add email@pm.me
		or
    gopass recipients add 1ABB2C1A

This command will reencrypt the files with all the previous keys plus the new one and sync with git.

## Graphical Interface
It is also possible to use Gopass with a electron based UI: [Gopass UI](https://github.com/codecentric/gopass-ui)
