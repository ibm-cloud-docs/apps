---
copyright:

  years: 2018

lastupdated: "2018-06-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Despliegue en un servidor virtual
{: #vsi-deploy}

Despliegue las apps de [{{site.data.keyword.cloud}} App Service ![Icono de enlace externo](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} en instancias del servidor virtual para permitir que la plataforma y las actividades de desarrollador de la infraestructura funcionen juntas y aumenten el control y la flexibilidad de la app.
{: shortdesc}

Una instancia de servidor virtual ofrece una mejor transparencia, previsibilidad y automatización para todos los tipos de carga de trabajo en comparación con otras configuraciones. Combínela con un servidor nativo para crear combinaciones de carga de trabajo exclusivas. Por ejemplo, puede crear lógica de base de datos de alto rendimiento o aprendizaje automático con configuraciones nativas y GPU en ejecución en un sistema operativo basado en Debian Linux.

## Antes de empezar
Para utilizar instancias virtuales, la cuenta de {{site.data.keyword.cloud_notm}} debe estar habilitada para la infraestructura. Para obtener más información, consulte [Actualice a infraestructura ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}.

## Despliegue a través de Terraform
Cualquiera de los kits de iniciación de App Service se puede desplegar en una instancia virtual creada de forma dinámica a través de [Terraform ![Icono de enlace externo](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, una infraestructura de código abierto como infraestructura de código. Para obtener más información, consulte [Documentación de Terraform ![Icono de enlace externo](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}.

## Habilitación del despliegue de conducto

Al crear un kit de iniciación que utiliza [{{site.data.keyword.cloud_notm}} App Service ![Icono de enlace externo](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}, se habilitará la instancia de servidor virtual. Una vez creada la app, podrá elegir dónde desea desplegarla. Los kits de iniciación están habilitados para dar soporte al despliegue utilizando una cadena de herramientas de Continous Delivery. Los kits de iniciación pueden destinarse a Kubernetes, Cloud Foundry e Instancias de servidor virtual. La cadena de herramientas incluye un repositorio de código fuente y un conducto de despliegue.

La opción del servidor virtual funciona en fases. En primer lugar, el código de la app está preparado y almacenado en un repositorio Git de GITLab y el código fuente crea una cadena de herramientas con un conducto. El conducto está definido para crear el código y empaquetarlo en un formato de gestor de paquetes de Debian. A continuación, Terraform proporciona una instancia virtual. Finalmente, la app se despliega, se instala y se inicia dentro de la imagen virtual en ejecución y su estado se valida.

El conducto falla en el primer uso porque necesita que se configure manualmente un conjunto de propiedades de cuenta de usuario. Estas propiedades no se pueden pasar en la cadena de herramientas que utiliza el código fuente GIT por motivos de seguridad. Debe configurar manualmente estos valores para permitir que la cadena de herramientas se complete satisfactoriamente.

Siga estos pasos para hacer que las propiedades del entorno sean visibles y habilitar el conducto con las propiedades de la cuenta de usuario.

1. En la página Detalles de la app, pulse **Ver cadena de herramientas**.
2. Pulse el mosaico **Delivery Pipeline**.
3. Pulse **Configurar etapa** en la etapa de compilación.
4. Pulse el separador **Variables de entorno** para ver las propiedades.
5. Cambie estas propiedades en el separador Variables de entorno para permitir que la cadena de herramientas se ejecute satisfactoriamente.

| Propiedad   | Descripción   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | La [clave de API de la infraestructura](#iaas-key) proviene de la consola de infraestructura. |
| `TF_VAR_ibm_sl_username` | El [nombre de usuario de la infraestructura](#user-key) que identifica la cuenta de infraestructura. |
| `TF_VAR_ibm_cloud_api_key` | La {{site.data.keyword.cloud_notm}} [clave de API de plataforma](#platform-key) se utiliza para permitir la creación del servicio. |
| `PUBLIC_KEY` | [Clave pública](#public-key) definida para permitir el acceso a la instancia de servidor virtual. |
| `PRIVATE_KEY` | [Clave privada](#public-key) definida para permitir el acceso a la instancia de servidor virtual. |
| `VI_INSTANCE_NAME` | Nombre generado automáticamente para la instancia de servidor virtual. |
| `GIT_USER` | Si establece el [estado de Terraform](#tform-state) para almacenar el estado del mandato apply, se necesitará el nombre de usuario de GITLab. |
| `GIT_PASSWORD` | Si establece el [estado de Terraform](#tform-state) para almacenar el estado del mandato apply, se necesitará la contraseña de GITLab. |
{: caption="Tabla 1. Variables de entorno a cambiar para la habilitación" caption-side="top"}

### Recuperación de la clave de API de infraestructura
{: #iaas-key}

Terraform requiere una clave de API de infraestructura para crear recursos de infraestructura. Siga estos pasos para recuperar una clave de infraestructura.

1. Vaya a la [lista de usuarios ![Icono de enlace externo](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} de la infraestructura o **Menú** > **Infraestructura** > **Cuenta** > **Lista de usuarios**.
2. Busque los detalles de los usuarios que están creando la cadena de herramientas y pulse `Ver` en la columna Clave de API o pulse `Generar`. Ambos pasos muestran la clave de API en un diálogo.
3. Copie la Clave de API y sustituya el valor de la configuración de la Cadena de herramientas `TF_VAR_ibm_sl_api_key`.

### Recuperación del nombre de usuario de la infraestructura
{: #user-key}

Para recuperar el nombre de usuario de la infraestructura, siga estos pasos.

1. Vaya a la [lista de usuarios ![Icono de enlace externo](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} de la infraestructura o **Menú** > **Infraestructura** > **Cuenta** > **Lista de usuarios**.
2. Pulse el usuario que desee que cree la cadena de herramientas.
3. Desplácese hacia abajo hasta la propiedad **Nombre de usuario de VPN**.
4. Corte y pegue este valor y sustituya la configuración de la Cadena de herramientas `TF_VAR_ibm_sl_username`.

### Recuperación de la clave de API de la plataforma
{: #platform-key}

Para permitir que Terraform cree servicios a nivel de plataforma como bases de datos y servicios de Compose, se necesita la clave de API de la plataforma. Siga estos pasos para recuperar una clave de plataforma.

1. Pulse **Menú** > **Panel de control** para asegurarse de que el usuario se encuentre en el panel de control de la plataforma.
2. Pulse **Gestionar** > **Seguridad** > **Claves de API de plataforma**.
3. Pulse **Crear**.
4. Especifique un nombre y una descripción y pulse **Crear**.
5. Cuando el diálogo se abra, pulse *Mostrar* para revisar la clave.
6. Copie y pegue la clave en el portapapeles o descargue la clave.
7. Sustituya el valor de la configuración de la cadena de herramientas `TF_VAR_ibm_cloud_api_key` por el valor generado.

### Generación de la clave pública y privada
{: #public-key}

Para permitir que la cadena de herramientas instale el empaquetado de Debian en la instancia del Servidor virtual, siga estos pasos.

1. En el cálculo del cliente, utilice las siguientes instrucciones para crear un [par de claves públicas y privadas ![Icono de enlace externo](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}.
2. Vaya a la [Vista de claves SSH de infraestructura ![Icono de enlace externo](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window} o **Menú** > **Infraestructura** > **Dispositivos** > **Gestionar** > **Claves SSH**.
3. Pulse **Añadir**.
4. Copie el contenido de la clave privada que ha creado anteriormente y péguelo en el contenido de la clave.
5. Dé un nombre a la clave y pulse **Añadir**.

### Habilitación del estado de Terraform
{: #tform-state}

Terraform soporta el almacenamiento del estado del mandato `apply` de Terraform. Este archivo de estado ejecuta el mandato `apply` una segunda vez para determinar si se ha modificado alguno de los archivos de configuración de terraform. Puede almacenar el estado en el repositorio GIT que ha gestionado la app y la configuración.

Para habilitar el almacenamiento del estado, configure las propiedades `GIT_USER` y `GIT_PASSWORD` en las variables de entorno de la cadena de herramientas. Para recuperar los valores, siga estos pasos:

1. En la vista Cadenas de herramientas, acceda al repositorio GIT desde la Herramienta de código.
2. En GIT Lab, pulse el **icono Perfil** y, a continuación, pulse **Valores**.
3. Pulse **Cuenta** y copie el nombre de usuario y sustituya el valor `GIT_USER`.
4. Pulse **Señal de acceso**.
5. Defina un nombre para la señal y, a continuación, pulse **Crear señal de acceso personal**.
6. Pulse el icono Copiar desde el campo `Su nueva señal de acceso personal` y sustituya el valor de `GIT_PASSWORD` en las propiedades de la cadena de herramientas.

El estado de Terraform se almacena en una rama denominada `terraform`, y no activa la ejecución del conducto si se ha modificado.


### Habilitación de operaciones GIT
{: #git-repo}

Cuando la app se despliega en {{site.data.keyword.cloud_notm}}, se creará un repositorio GIT Lab para alojar el código para la gestión de código fuente. Puede utilizar las operaciones GIT para permitir que los equipos funcionen y entreguen cambios a la app. Las carpetas incluidas en este repositorio y una explicación de su contenido.

#### Carpeta Debian
{: #debian-folder}

La carpeta `debian` contiene la configuración necesaria para permitir el empaquetado de la app en un [paquete Debian. ![Icono de enlace externo](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}

#### Carpeta Terraform
{: #terraform-folder}

La carpeta `terraform` contiene la configuración para la infraestructura como código que se puede utilizar para suministrar recursos de infraestructura. El archivo `main.tf` es el origen principal para cambiar las opciones para la configuración de terraform.

```
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

También puede suministrar servidores nativos con terraform. Para obtener más información, consulte [Documentación del proveedor de IBM Terraform ![Icono de enlace externo](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} y [Repositorio GIT del proveedor de IBM Terraform ![Icono de enlace externo](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}.

`variables.tf` se puede utilizar para cambiar el centro de datos de destino para crear la instancia virtual. Para ver la lista de centros de datos definidos en la plataforma, consulte [Centros de datos ![Icono de enlace externo](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

De forma predeterminada, el archivo de terraform está configurado para Washington y `wdc04`.

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Comprensión de las etapas de la cadena de herramientas
{: #toolchain-stages}

La cadena de herramientas muestra el despliegue de la infraestructura y de la app en un único conducto. Desglose la infraestructura como parte de código en un conducto y el despliegue de apps en otro conducto.

La cadena de herramientas se desglosa en las etapas siguientes:

1. La Etapa de compilación clona el repositorio GIT y empaqueta el código en un paquete de Debian.
2. La Etapa de planificación de Terraform prepara un plan de terraform.

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. La Etapa de aplicación de Terraform aplica la configuración de terraform y espera hasta que la dirección IP del servidor virtual esté disponible.

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. La Etapa de despliegue, instalación e inicio traslada el paquete de Debian compilado en la primera etapa al servidor virtual en ejecución, lo instala y luego lo inicia.
5. La Etapa de comprobación de estado valida que el punto final de estado esté disponible en la app y luego completa el conducto.

Para acceder a la app una vez que se inicie, compruebe los registros de la Etapa de comprobación de estado. Pulse los enlaces de URL listados en los registros que muestran la dirección IP y el puerto de la app.
