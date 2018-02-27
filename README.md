# Exercício 1 de Kubernetes
1 - Criar um deployment para o nginx com a seguintes caracteristas:

    Replicas 5

    Port 80 TCP

    Volume para o /usr/share/nginx/html

    index personalisada

    Deve rodar em UK
2 - Criar um service do tipo nodeport e com a porta 31212 bindando no host

3 - Exportar o diretorio /k8s via nfs

4 - criar um PV com 150M utilizando o nosso fs NFS

5 - criar um pvc utilizando o nosso fs NFS

6 - montar o volume no pod em /usr/share/nginx/html com o index personalizado

7 - Criar um label indicando se eh producao ou dev e outro indicando o nome da app.

8 - setar um label dc=BR para o node-1, dc=USA node-2 e dc=UK node-3

