CONFIGURAÇÃO DO FIREBASE — LEIA ANTES DE PUBLICAR

Este projeto usa Cloud Functions para gerar e validar o código secreto no servidor.
Assim o motoboy não recebe o código secreto no documento do pedido.

1) Instale Node.js e Firebase CLI.
2) No terminal, entre nesta pasta firebase/functions e rode npm install.
3) Inicialize o Firebase no diretório firebase (firebase init), escolhendo Firestore e Functions.
   Use JavaScript e Node 20 se a ferramenta oferecer essa opção.
4) Publique as regras: firebase deploy --only firestore:rules
5) Publique as funções: firebase deploy --only functions

Antes de usar com clientes reais, implemente também:
- Cadastro administrativo seguro dos motoboys e atribuição dos pedidos.
- Regras de leitura de courierLocations para permitir somente o cliente dono do pedido e o admin.
- Validação do papel courier com custom claims ou documento de perfil protegido.
- Limite de tentativas do código e fluxo de suporte.
- Configuração de pagamentos e WhatsApp.
- Política de privacidade e consentimento de localização.

A função createCustomerOrder salva o pedido e cria um segredo separado.
A função getCustomerDeliveryCode permite ao dono recuperar o código.
A função confirmDelivery valida o código e finaliza o pedido.
