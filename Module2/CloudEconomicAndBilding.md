# AWS Module 2 - Cloud Economics and Billing

## 1. Fundamentals of Pricing

### 1. When can you stop paying for an AWS service?

Puedes dejar de pagar por un servicio de AWS cuando dejas de utilizarlo y eliminas o detienes los recursos que has creado, dependiendo del servicio.

### 2. What is the charge for introducing data into AWS (Inbound Data)?

La transferencia de datos de entrada a AWS es generalmente gratuita.

### 3. Which AWS services incur costs?

La mayoría de los servicios de AWS pueden generar costes cuando utilizas sus recursos. Estos dependen del servicio, de la cantidad de recursos utilizados y del modelo de precios.

### 4. True or False: A free AWS service will never incur any charges.

**Falso.** 

`Un servicio puede ser gratuito bajo determinadas condiciones o límites, pero puede generar cargos si se superan esos límites o se utilizan otros recursos que sí tienen coste.`


## 2. Total Cost of Ownership

### 1. What is TCO (Total Cost of Ownership)?

El TCO es el coste total de poseer y utilizar una solución tecnológica. No incluye únicamente el coste inicial, sino también gastos como el mantenimiento, la infraestructura, la electricidad, el hardware, el software y la administración.


## 3. AWS Organizations

### 1. In your own words, explain what AWS Organizations is and what it is used for.

Es un servicio de AWS que permite a una empresa gestionar cuentas de AWS. Se utiliza para organizar las cuentas, administrar permisos y políticas y controlar los costes de toda la organización.

### 2. What is an OU (Organizational Unit)? Can an account belong to more than one OU?

Es un grupo de cuentas de AWS dentro de una organización. Se utiliza para organizar las cuentas y aplicar políticas a grupos de cuentas.

No, una cuenta de AWS solo puede pertenecer a una OU a la vez.

### 3. Can multiple users use a single AWS account using AWS IAM?

Sí. AWS IAM permite crear varios usuarios, grupos y roles para que diferentes personas puedan acceder a una misma cuenta de AWS con diferentes permisos.

### 4. Order the following steps when implementing AWS Organizations

El orden correcto es:

1. B) Crear la organización desde la cuenta activa de AWS como cuenta principal/de administración.
2. D) Crear dos Organizational Units (OUs) y colocar las cuentas miembro dentro de esas OUs.
3. A) Crear las Service Control Policies (SCPs).
4. C) Probar las políticas de la organización realizando pruebas, cambiando de roles o utilizando IAM Policy Simulator.


## 4. Billing and Costs

### 1. What does the "Monthly Spend to Date by Service" graph on the AWS Billing dashboard show?

Muestra cuánto dinero se ha gastado hasta el momento durante el mes actual, dividido según los diferentes servicios de AWS utilizados.

### 2. What color are the icons for AWS cost management tools?

Los iconos de las herramientas son de color morado.

### 3. How many months of cost data are available in AWS Cost Explorer?

AWS Cost Explorer permite consultar 14 meses de datos históricos.

### 4. In which service can you create notifications for when your monthly budget is exceeded or when your estimated costs exceed your budget?

Estas notificaciones se pueden configurar mediante el servicio AWS Budgets.


## 5. Technical Support

### 1. What is AWS Trusted Advisor used for?

AWS Trusted Advisor analiza el entorno de AWS y proporciona recomendaciones para mejorar la optimización de costes, el rendimiento, la seguridad, la tolerancia a fallos y los límites de servicio.