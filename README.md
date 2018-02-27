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

# Resultados

    root@vm01:~/exercicio1# kubectl get deployment,pods,rs,ds -l dc=UK
    NAME                             READY     STATUS    RESTARTS   AGE
    po/exercicio1-7c9c7c44cf-4n9nv   1/1       Running   0          13m
    po/exercicio1-7c9c7c44cf-6fcl9   1/1       Running   0          13m
    po/exercicio1-7c9c7c44cf-7xvmw   1/1       Running   0          13m
    po/exercicio1-7c9c7c44cf-jdgxw   1/1       Running   0          13m
    po/exercicio1-7c9c7c44cf-rxxcv   1/1       Running   0          13m

    NAME                       DESIRED   CURRENT   READY     AGE
    rs/exercicio1-7c9c7c44cf   5         5         5         13m

    root@vm01:~/exercicio1# kubectl get deployment,pods,rs,ds -l dc=US
    No resources found.

    root@vm01:~/exercicio1# kubectl get deployment,pods,rs,ds -l dc=BR
    No resources found.

    root@vm01:~/exercicio1# kubectl get deployment,pods,rs,ds -l dc=BR -o wide
    No resources found.

    root@vm01:~/exercicio1# kubectl get deployment,pods,rs,ds -l dc=UK -o wide
    NAME                             READY     STATUS    RESTARTS   AGE       IP          NODE
    po/exercicio1-7c9c7c44cf-4n9nv   1/1       Running   0          14m       10.38.0.1   vm03
    po/exercicio1-7c9c7c44cf-6fcl9   1/1       Running   0          14m       10.38.0.5   vm03
    po/exercicio1-7c9c7c44cf-7xvmw   1/1       Running   0          14m       10.38.0.4   vm03
    po/exercicio1-7c9c7c44cf-jdgxw   1/1       Running   0          14m       10.38.0.2   vm03
    po/exercicio1-7c9c7c44cf-rxxcv   1/1       Running   0          14m       10.38.0.3   vm03

    NAME                       DESIRED   CURRENT   READY     AGE       CONTAINERS   IMAGES    SELECTOR
    rs/exercicio1-7c9c7c44cf   5         5         5         14m       nginx        nginx     pod-template-hash=3757370079,run=nginx
