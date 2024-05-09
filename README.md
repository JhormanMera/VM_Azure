# VM_Azure
### Jhorman Mera
Azure VM using Terraform

* ## Requerimientos:
    * Sistema operativo con terraform instalado:
        * [Instalar terraform en linux](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
        * [Instalar Terraform en Windows](https://learn.microsoft.com/es-es/azure/developer/terraform/get-started-windows-bash?tabs=bash) 

    * Azure Cli instalado con la sesión de azure iniciada, para esto se puede seguir la guía de [instalar azure-cli](https://learn.microsoft.com/es-es/cli/azure/install-azure-cli-linux?pivots=apt) de hashicorp
    * Archivo ````terraform.tfvars```` con los valores para las variables definidas en el archivo ````variables.tf````

* ## Pasos a seguir:

* Después de haber definido la IaC usando terraform, donde se obtiene una ip pública para nuestra Vm y se le habilita la gestión por ssh en el archivo [main](main.tf) podemos ver que ese contiene:

    * Azure Resource Group.
    * Azure Virtual Network.
    * Azure Subnet.
    * Azure Public IP.
    * Azure Network Interface.
    * Azure Network Security Group.
    * Azure Network Interface Security
    * Group Association.
    * Azure Network Security Rule.
    * Azure Virtual Machine.
        * Storage OS Disk.

* El archivo [variables](variables.tf) contiene las definiciones de variables que serán utilizadas en los archivos de configuración de Terraform (como [main](main.tf), [outputs](outputs.tf), etc.). Estas variables pueden ser utilizadas para parametrizar la configuración de la infraestructura y permitir una mayor flexibilidad y reutilización del código.

* El archivo [terraform](terraform.tfvars) un archivo de variables específico de Terraform que se utiliza para definir valores específicos para las variables declaradas en los archivos de configuración de Terraform, como el archivo de [variables](variables.tf). Este archivo es opcional, pero es una práctica común para proporcionar valores específicos para las variables en lugar de especificarlos directamente en los comandos de Terraform o en otros archivos.

* ## Comandos

1. Preparar el directorio de trabajo para trabajar con terraform ````terraform init````

![init](images/init.png)

2. Validar la configuración de terraform ````terraform validate````

![validate](images/validate.png).

3. Validar y mostrar los cambios requeridos para aplicar la configuración de la infraestructura ````terraform plan````

![plan_1](images/plan_1.png)
![plan_2](images/plan_2.png)

4. Aplicar un formateo en el archivo de definición que se crea con terraform ````terraform fmt````
5. Crear la infraestructura ````terraform apply````

![apply_1](images/apply_1.png)

Es necesario estar atentos a esta parte del aprovisionamiento para confirmar los cambios a realizar por terraform escribiendo ```yes``` en la consola

![apply_2](images/apply_2.png)
![apply_3](images/apply_3.png)

### Evidencia del dashboard de Azure

![azure_dashboard](images/azure_dashboard.png)

6. En caso de necesitar eliminar la infraestructura, se usa el comando ````terraform destroy````

![destroy_1](images/destroy_1.png)
![destroy_2](images/destroy_2.png)

Nota: Se debe eliminar manualmente el disco que estaba usando la Vm para poder eliminar posteriormente el grupo de recursos

![destroy_3](images/destroy_3.png)