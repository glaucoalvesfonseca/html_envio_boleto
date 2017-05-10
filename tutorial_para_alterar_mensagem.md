# TUTORIAL

**Passo 1.** A tabela `SNT_MODELO` abriga o modelo HTML que é enviado aos clientes da Unimed. Ela pode ser acessada utilizando o comando:

```sql
SELECT * FROM SNT_MODELO for update
```
*Obs.: não esqueça de colocar o `for update` no final da Query, caso contrário não será possível alterar o HTML.*
 
**Passo 2.** Acesse a linha `HTML_EMAIL_BOLETO_ARARUAMA` clicando sobre o ícone de reticências da coluna "XSLT", onde está escrito a informação `<Long>`;
 
**Passo 3.** Na janela que abrir, selecione a aba `TEXT`. Lá estará o HTML utilizado no corpo do e-mail do boleto.
 
**Passo 4.v Ao realizar as alterações, clique sobre o botão "OK" para fechar a janela. Em seguida, clique sobre o botão "Post Changes" - que possui um símbolo de um sinal de correto verde. Por fim, clique sobre o cadeado e commit as alterações pressionando F10 ou clicando sobre o ícone "Commit changes", que possui um ícone de uma seta verde pra baixo sobre um disco.
 
## ALTERAÇÕES NO SERVIDOR
 
As imagens presentes no HTML estão hospedadas no servidor de Intranet. A forma de configuração é semelhante a assinatura de e-mail.
 
**Passo 1.** O diretório onde os arquivos se encontram é /etc/nginx/conf.d;
 
**Passo 2.** Caso precise adicionar, remover ou alterar arquivos, coloque-os nesse diretório. Será preciso também alterar o arquivo `assinatura.conf`, o qual cria um alias que permite o acesso de tal arquivo via HTTP. A configuração para cada arquivo deve seguir o modelo abaixo:
 
`location /downloads/NOME_DO_ARQUIVO.extensão { alias /etc/nginx/conf.d/NOME_DO_ARQUIVO.extensão; }`
 
*Obs.: o nome do arquivo não pode conter espaços.*
 
**Passo 3.** Após alteração do arquivo "assinatura.conf", reinicialize o serviço Nginx com o comando abaixo. É preciso ter acesso administrativo para executá-lo:
``` 
service nginx restart
```
 
**Passo 4.** Feito isso com sucesso, o arquivo pode ser acessado via web.
