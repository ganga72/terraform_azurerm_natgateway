Terraform Module to provision an Azure NAT Gateway to provide outbound access to the internet for Azure Virtual Machines

Example usage
terraform {
  required_version = ">= 1.3.0"

  required_providers {
    azurerm = {
      version = ">= 3.71.0"
      source  = "hashicorp/azurerm"
    }
  }
}

provider "azurerm" {
  features {}
}

module "natgateway" {
  source  = "carlzxc71/natgateway/azurerm"
  version = "1.0.8"

    // Required variables
    existing_rg_name = "rg-prod-sc-core"
    
    // Optional variables
    nat_gw_name      = "natgw-prod-sc-core"
    nat_gw_sku_name  = "Standard"
    location         = "Sweden Central"
    pip_sku_name     = "Standard"
    pip_name         = "pip-nat-gateway"
}
Requirements
Name	Version
terraform	>= 1.3.0
azurerm	>= 3.71.0
Providers
Name	Version
azurerm	>= 3.71.0
Modules
No modules.

Resources
Name	Type
azurerm_nat_gateway.this	resource
azurerm_nat_gateway_public_ip_association.this	resource
azurerm_public_ip.this	resource
azurerm_resource_group.this	data source
Inputs
Name	Description	Type	Default	Required
existing_rg_name	value for the name of an existing resource group	string	n/a	yes
location	value for the location of the nat gateway	string	"West Europe"	no
nat_gw_name	value for the name of the nat gateway	string	"nat-Gateway"	no
nat_gw_sku_name	value for the sku name of the nat gateway	string	"Standard"	no
pip_name	value for the name of the public ip	string	"pip-nat-gateway"	no
pip_sku_name	value for the sku name of the public IP	string	"Standard"	no
Outputs
Name	Description
name	The name of the nat gateway
pip_address	The address of the public ip
