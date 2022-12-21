# Comandos de terminal para CodeCommit

1. Crear llaves en IAM
2. Configurar Aws
```
aws configure
```
3. Crear repositorio
```
aws codecommit --create-repository --repository-name mi_repositorio
```
4. Listar repositorios
```
aws codecommit --list-repositories
```
5. Clonar Repositorio
```
aws codecommit --get-repositories --repository-name mi_repositorio
```
6. Borrar repositorio
```
aws codecommit --delete-repository --repository-name mi_repositorio
```

