#!/bin/bash

STORAGE_ACCOUNT="storageaccountname"
RESOURCE_GROUP="resource-group-name"
CONTAINER="data-container"
OUTPUT="sftp_credentials.csv"

echo "username,password,homeDirectory" > $OUTPUT

echo "Criando estrutura base..."

az storage fs directory create \
 --account-name $STORAGE_ACCOUNT \
 --file-system $CONTAINER \
 --name config \
 --auth-mode login

az storage fs directory create \
 --account-name $STORAGE_ACCOUNT \
 --file-system $CONTAINER \
 --name inbound \
 --auth-mode login

az storage fs directory create \
 --account-name $STORAGE_ACCOUNT \
 --file-system $CONTAINER \
 --name outbound \
 --auth-mode login

echo "Estrutura criada."

while read USER
do

 echo "----------------------"
 echo "Configurando: $USER"

 IN_DIR="inbound/$USER"
 OUT_DIR="outbound/$USER"

 az storage fs directory create \
  --account-name $STORAGE_ACCOUNT \
  --file-system $CONTAINER \
  --name $IN_DIR \
  --auth-mode login

 az storage fs directory create \
  --account-name $STORAGE_ACCOUNT \
  --file-system $CONTAINER \
  --name $OUT_DIR \
  --auth-mode login

 echo "Criando usuário SFTP..."

 az storage account local-user create \
  --account-name $STORAGE_ACCOUNT \
  --resource-group $RESOURCE_GROUP \
  --user-name $USER \
  --home-directory $IN_DIR \
  --permission-scope permissions=rw service=blob resource-name=$CONTAINER \
  --has-ssh-password true \
  --has-ssh-key false \
  --has-shared-key false > /dev/null

 echo "Gerando senha..."

 PASS=$(az storage account local-user regenerate-password \
  --account-name $STORAGE_ACCOUNT \
  --resource-group $RESOURCE_GROUP \
  --user-name $USER \
  --query sshPassword -o tsv)

 echo "$USER,$PASS,$IN_DIR" >> $OUTPUT

 echo "Usuário $USER criado."

done < users.txt

echo "----------------------"
echo "Processo finalizado"
echo "Credenciais salvas em $OUTPUT"
