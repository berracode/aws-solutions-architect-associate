# IAM 

## Users and groups
- IAM: Identity and access management, servicio global
- Root account, se crea por defecto, no debería ser usado
- Los usuarios son personas dentro d euna organización y pueden ser agrupados
- Los grupos solo contiene usuarios, no otros grupos
- los usuarios no tienen que pertenecer a un grupo, y los usuarios pueden pertenecer a multiples grupos.

![grupos](../docs/02.%20iam-awscli/users-groups.png)

## Permissions

- A los usuarios y grupos se les puede asignar documentos JSON llamados POLICIES (IAM policy)
- Las politicas o policies definen permisos de los usuarios
- Principio de privilegio minimo.

## IAM POLICIES Structure

Consiste en:
- Version: lenguaje de version de la politica, siempre ha sido 2012-10-17
- Id: id de la politica (opcional)
- Statement: un arreglo de statements (1 o más, es requerido)

Statement, consiste en:
- Sid: id del statement (opcional)
- Effect: si el statement permite o niega un acceso (Allow, deny)
- Principal: account/user/role al cual esa politica aplica
- Action: lista de acciones que esa politica permite o deniega.
- Resource: lista de recursos a los cuales la acción aplica.
- Conditional: condición para saber cuando la politica hace efecto (opcional)

![politicas](../docs/02.%20iam-awscli/iam-policies.png)

### ¿Qué es un recurso en AWS?

Un recurso en AWS es una entidad que puedes administrar dentro de un servicio de AWS. Por ejemplo, dentro del servicio S3, un **recurso puede ser un bucket o un objeto dentro de un bucket**. Dentro de EC2, un recurso podría ser una instancia, un volumen de almacenamiento EBS, o un grupo de seguridad.

Ejemplo:

1. **Recurso especifico:** Permitir acciones sobre un bucket S3 llamado mi-bucket.

```json
"Resource": "arn:aws:s3:::mi-bucket"
```

2. **Todos los recursos de un servicio:** Permitir acciones sobre todos los buckets de S3

```json
"Resource": "arn:aws:s3:::*"
```

### ¿qué es un ARN?

ARNs: Identificadores de Recursos.

En AWS, los recursos se identifican mediante un ARN (Amazon Resource Name), que es un formato estándar que describe un recurso. 

Ejemplo de ARN para un bucket S3:
```json
"Resource": "arn:aws:s3:::mi-bucket"
```

Formato general:
```sh
arn:partition:service:region:account-id:resource
```

#### Ejemplo de politica propia:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Action": [
                "iam:ListUsers",
                "iam:GetUser"
            ],
            "Resource": [
                "arn:aws:iam::ACCOUNT-ID:user/*"
            ]
        }
    ]
}

```

#### Significado
esta politica permite listar y obtener usuarios, y aplica al recurso **user** de iam, es decir no a roles ni grupos, ni ningun otro recurso de IAM, entonces todo usuario que tenga esta politica puede listar usuarios y obtener usuarios, no más.






