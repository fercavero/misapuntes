# Crear un usuario de IAM con pemisos de Administrador

1. Buscar IAM en la barra de búsqueda
2. Ir a la sección de usuarios
3. Hacer click en añadir Usuario
4. Crear el usuario k8-admin
5. Atacharle politicas directamente
6. Seleccionar la politica AdministratorAccess
7. Hacer click en crear usuario
8. Habilitar Access Key para poder trabajar con aws cli


# Preparar un máquina EC2 que hara de bastion

1. Navegar a EC2
2. Lanzar un nueva instancia
3. Seleccionar Amazon linux 2 AMI
4. El tipo de insrtancia dejarlo en t2.micro
5. Editar los deatlles de la instancia
	- Dejar por defecto la red
	- Dejar por defecto la subnet
	- Habilitar que auto-asigne la ip publica
6. El resto de cosas lo dejamos por defecto
7. Creamos un naueva llave PEM
8. Una vez que la instancia este healthy nos conectamos a ella desde el mismo explorador
9. Vemos la version que tenmos de aws cli
```bash
aws -version
```
10. DEscargamos la version 2 de aws cli
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
11. MIramos donde tenmos aws instalado con el siguiente comando
```bash

which aws
#Nos deberia retornar la ruta /usr/bin/aws

```

12. La actualizamos
```bash
sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update
```

20. Chequeamos d enuevo la version
```bash
aws --version
```

21. Configuramso la CLI
```bash
aws configure
```

22. Pegamos unuestras access key y secret key seleccionamos la reginon por defecto y la salida


# INSTALAR Y CONFIGURAR CLUSTER EKS

# Descargamos kubectl

```bash
# Descargamos kubctl

curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.16.8/2020-04-16/bin/linux/amd64/kubectl

#Le damos permisos a kubectl

sudo chmod +x ./kubectl

# Copiamos el binario a un directorio y lo metemos en nuestro path para que podamos usarlo desde cualquier punto de la terminal

mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin

#Vemos la version que hemos descargado
kubectl version --short --client

```


# Instalamos eksctl

```bash 

#Descaragamos eksctl y lo descomprimimos en el directotio /tmp
curl --location
"https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname - s)_amd64.tar.gz" | tar xz -C /tmp

#Movemos eksctl a /usr/local/bin
sudo mv -v /tmp/eksctl /usr/local/bin

#Vemos la version de eks que hemos descargado
eksctl version

```

# Si estamos en una máquina de amazon podemos exportarnos la region a una variable de entorno

```bash
#Leemos la metadata del servidor para saber la region
export AWS_REGION=$(curl --silent http://169.254.169.254/latest/meta-data/placement/region) && echo $AWS_REGION 
```

# Comando para deplegar un cluster de kubernetes con eksctl

```bash
eksctl create cluster \
--name mi-cluster \
--nodegroup-name mis-nodos \ 
--node-type t3.small \ 
--nodes 3 \ 
--nodes-min 1 \ 
--nodes-max 4 \ 
--managed \ 
--version 1.23 \ 
--region ${AWS_REGION}
```

A continuación muestro lo que significa cada flag
- eksctl create cluster --> Crea un nuevo cluster en EKS.
	- ** --name mi-cluster** le damos un nombre al cluster en este caso se llamara 'mi-cluster'.
	- ** --nodegroup-name** mis-nodos le damos un nombre al node group.
	- ** --node-type t3.small** ls damos el tamaño de instancia que tendra cada nodo.
	- --nodes 3 el número de nodos que se desplegaran durante el despliegue.
	- --nodes-min 1 configuramos el número míminimo de nodos para el auto escalado group de nuestro node-group.
	- --nodes-max 4 configuramos el número máximo de nodos que tendremos en el auto escalado.
	- --managed creara el node group gestionado por amazon
	- --version 1.23 le decimos la version de kubernetes que queremos desplegar
	- --region AWS_REGION le decimos en que region debe desplegar nuestro cluster de kubernetes.

Este comando creara un fichero de configuración en ~/.kube/config

# NOTA:
	El comando anterior nos añadira system:masters en la configuración de kubernetes RBAC(Role Based Access Control)

Una vez lanzamos este comando se lanzaran un par de stacks de cloudformation que crearan la red del cluster y todos los roles y politicas necesarios para que el cluster funcione
