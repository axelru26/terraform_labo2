# Explication Infrastructure
## Fichier main.tf
### Random Pet Resource:
Cette ressource génère un nom de ressource aléatoire (utilisant un préfixe défini par la variable resource_group_name_prefix). Ce nom de ressource sera utilisé ultérieurement pour créer un groupe de ressources Azure.

### Azure Resource Group:
Cette ressource crée un groupe de ressources Azure avec le nom généré aléatoirement à partir de la ressource random_pet. Le groupe de ressources est créé dans l'emplacement spécifié par la variable resource_group_location.

### Azure Virtual Network:
Cette ressource crée un réseau virtuel Azure avec l'adresse IP 10.0.0.0/16 dans le groupe de ressources et l'emplacement spécifiés.

### Azure Subnet:
Cette ressource crée un sous-réseau nommé "mySubnet" dans le réseau virtuel créé précédemment avec l'adresse IP 10.0.1.0/24.

### Azure Public IP Address:
Cette ressource crée une adresse IP publique dynamique nommée "myPublicIP" dans le groupe de ressources et l'emplacement spécifiés.

### Azure Network Security Group (NSG) and Rule:
Cette ressource crée un groupe de sécurité réseau avec une règle permettant le trafic SSH entrant.

### Azure Network Interface:
Cette ressource crée une interface réseau avec une configuration IP dynamique, associée au sous-réseau créé précédemment.

### Association de NSG à l'Interface Réseau:
Cette ressource associe le groupe de sécurité réseau à l'interface réseau, appliquant ainsi la règle permettant le trafic SSH entrant.

### Random ID for Storage Account:
Cette ressource génère un identifiant aléatoire de 8 octets, en fonction du nom du groupe de ressources Azure.

### Azure Storage Account:
Cette ressource crée un compte de stockage Azure avec un nom généré dynamiquement (utilisant l'identifiant aléatoire) et le type de stockage LRS (Locally Redundant Storage).

### Azure Linux Virtual Machine:
Cette ressource crée une machine virtuelle Linux dans le groupe de ressources, avec l'interface réseau et d'autres configurations spécifiées.

## Fichier outputs.tf
### Nom du Groupe de Ressources en Sortie :
Cette instruction output définit une sortie appelée "resource_group_name" avec la valeur du nom du groupe de ressources (azurerm_resource_group.rg.name). Après l'exécution du plan Terraform, cette valeur peut être consultée en utilisant la commande terraform output resource_group_name.

### Adresse IP Publique de la Machine Virtuelle en Sortie :
Cette instruction output définit une sortie appelée "public_ip_address" avec la valeur de l'adresse IP publique de la machine virtuelle (azurerm_linux_virtual_machine.my_terraform_vm.public_ip_address). Après l'exécution du plan Terraform, cette valeur peut être consultée en utilisant la commande terraform output public_ip_address.

## Fichier providers.tf
### Bloc Terraform :
Ce bloc Terraform définit la version minimale requise de Terraform (>=0.12) et spécifie les fournisseurs (providers) requis pour ce projet. Dans ce cas, les fournisseurs nécessaires sont azure/azapi (version 1.5 ou supérieure), hashicorp/azurerm (version 2.0 ou supérieure) et hashicorp/random (version 3.0 ou supérieure).

### Bloc de Configuration du Fournisseur Azurerm :
Ce bloc de configuration définit le fournisseur (provider) Azurerm. Dans ce cas, il n'y a pas de configuration spécifique définie, mais le bloc features {} est inclus. Ce bloc est utilisé pour activer ou désactiver certaines fonctionnalités spécifiques du fournisseur. Dans l'exemple donné, aucune fonctionnalité spécifique n'est activée.

## Fichier variable.tf
### Variable resource_group_location :
Cette variable est de type chaîne de caractères (string). Elle a une valeur par défaut de "westeurope" et est utilisée pour spécifier l'emplacement (région Azure) du groupe de ressources.

### Variable resource_group_name_prefix :
Cette variable est également de type chaîne de caractères (string). Elle a une valeur par défaut de "rg" et est utilisée comme préfixe pour le nom du groupe de ressources. Un identifiant aléatoire sera ajouté à ce préfixe pour garantir l'unicité du nom du groupe de ressources dans votre abonnement Azure.

### Variable username :
Cette variable est de type chaîne de caractères (string). Elle est utilisée pour spécifier le nom d'utilisateur du compte local qui sera créé sur la nouvelle machine virtuelle. Par défaut, la valeur est définie sur "azureadmin".

## Screen de l'infrastructure
* LIEN GITHUB VERS SCREEN INFRA
