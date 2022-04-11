os valores entre -> <- são comandos.
exemplo: rode o comando -> yarn add firebase-tools <-

rodar comando: para instalar o CLI
npm install -g firebase-tools
yarn add firebase-tools

O comando abaixo força o windows aceitar execução de scrips por arquivos, para esete usuário atual.
-> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser <-

rode -> firebase <- se aparecer varios dados com comandos é que deu tudo certo. Caso aconteça erro de script, rode o comando acima.
depois -> firebase login <- para você fazer login na sua conta. Vai abrir uma pagina na web e você logar.

Entrar no console do firebase ir em visão geral -> abaixo do nome do projeto tem uma pequena tabela com o nome app,
abra -> abra configurações -> procure a parte de configuração sdk e clique em CDN, copie o codigo.

Feito isso você precisa adicionar o que irá usar. No codigo copiado é passado uma url
https://firebase.google.com/docs/web/setup#available-libraries
acesse ela e adicione o que precisa.

essa linha deve sempre ficar em primeiro na parte dos import.
import { initializeApp } from "https://www.gstatic.com/firebasejs/9.6.10/firebase-app.js";
ou 
<script src="https://www.gstatic.com/firebasejs/8.4.3/firebase-app.js"></script>

É preciso liberar o tipo de auth na conta firebase. ( entre no projeto que você deseja ativar o auth, vá em
AUTHENTICATION depois em PROVIDERS e então escolha e ative os tipos de provedores. )

depois vá em : https://firebase.google.com/docs/auth?authuser=1
neste link vocÊ encontrará métodos já prontos para uso. Escolha a plataforma e siga.
Para nosso caso vamos escolher WEB -> PASSWORD AUTHENTICATION
* Create a password-based account

codigo firebase ( Ao passar um email e senha será criado uma nova conta.) 
firebase.auth().createUserWithEmailAndPassword(email, password)
  .then((userCredential) => {
    // Signed in 
    var user = userCredential.user;
    // ...
  })
  .catch((error) => {
    var errorCode = error.code;
    var errorMessage = error.message;
    // ..
  });

  para logar: Nesse passo já deve existir uma conta criada.

  firebase.auth().signInWithEmailAndPassword(email, password)
  .then((userCredential) => {
    // Signed in
    var user = userCredential.user;
    // ...
  })
  .catch((error) => {
    var errorCode = error.code;
    var errorMessage = error.message;
  });

  