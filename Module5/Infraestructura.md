
# Práctica AWS: Diseño de infraestructura de NeoShop

## 1. Definición del bloque de red

**¿Qué es lo primero que debemos crear en AWS para aislar completamente los recursos de la nube?**

Una VPC (Virtual Private Cloud).

Esta es una red virtual privada dentro de AWS que permite organizar y aislar los recursos de nuestra infraestructura, como servidores, bases de datos y subredes.

## 2. Bloque CIDR `10.0.0.0/16`

**¿Cuántas direcciones IP tenemos disponibles?**

El bloque CIDR `10.0.0.0/16` contiene:

- `2^(32-16) = 2^16 = 65.536` direcciones IP.
- AWS reserva 5 direcciones IP en cada subred, por lo que no todas pueden asignarse a los recursos.

**¿Qué recursos u operaciones consumen direcciones IP?**

Las direcciones IP se utilizan para identificar y permitir la comunicación entre recursos de la red, por ejemplo:

- Servidores web y de aplicaciones.
- Instancias EC2.
- Bases de datos.
- Interfaces de red.
- Balanceadores de carga y otros servicios de red.

**¿Es necesario disponer de tantas direcciones IP?**

No necesariamente. Para una startup como NeoShop, 65.536 direcciones pueden ser excesivas al principio. Sin embargo, un bloque `/16` permite ampliar la infraestructura en el futuro sin tener que rediseñar la red.

## 3. Segmentación de la red: subred pública y privada

Debemos crear dos subredes dentro de la VPC, cada una con al menos 250 direcciones IP disponibles.

| Subred | Bloque CIDR | Direcciones totales | Direcciones utilizables en AWS |
|---|---|---:|---:|
| Pública | `10.0.1.0/24` | 256 | 251 |
| Privada | `10.0.2.0/24` | 256 | 251 |

**¿Qué recursos colocaremos en cada subred y por qué?**

- **Subred pública:** el servidor web y el servidor temporal de pruebas, si necesitan acceso directo desde Internet.
- **Subred privada:** la base de datos y los servidores internos de la aplicación.

## 4. Tráfico y tablas de enrutamiento

**¿Cuál de las dos tablas necesita una ruta hacia el Internet Gateway (`0.0.0.0/0`)?**

La tabla de la **subred pública**, porque necesita permitir el tráfico hacia Internet. 

### Tabla de enrutamiento de la subred privada

| Destino | Target |
|---|---|
| `10.0.0.0/16` | Local |

### Tabla de enrutamiento de la subred pública

| Destino | Target |
|---|---|
| `10.0.0.0/16` | Local |
| `0.0.0.0/0` | Internet Gateway (IGW) |

## 5. Conectividad y acceso externo

### A. ¿Qué tipo de IP asignarías al servidor temporal de pruebas de los desarrolladores y por qué?

Le asignaría una **IP pública dinámica**, esto permite que el servidor sea accesible desde Internet mientras se realizan las pruebas, sin necesidad de reservar una dirección permanente. 

### B. ¿Qué tipo de IP asignarías al servidor web de producción y qué ventaja ofrece ante un fallo de hardware?

Le asignaría una **Elastic IP**, que es una dirección IPv4 pública estática de AWS.

Sus principales ventajas son:

- Mantiene la misma dirección IP pública aunque se sustituya la instancia.
- Permite asociar la dirección a otra instancia compatible en caso de fallo.
- Evita tener que cambiar constantemente la dirección IP pública del servidor.
