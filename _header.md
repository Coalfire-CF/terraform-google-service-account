![Coalfire](coalfire_logo.png)


# Google Cloud Service Account Terraform Module

## Description

This module allows easy creation of one or more service accounts, and granting them basic roles. Coalfire has tested this module with Terraform version 1.5.0 and the Hashicorp Google provider versions 4.70 - 5.0. 

FedRAMP Compliance: High

## Resource List

The resources/services/activations/deletions that this module will create/trigger are:

- one or more service accounts
- optional project-level IAM role bindings for each service account
- one optional billing IAM role binding per service account, at the organization or billing account level
- two optional organization-level IAM bindings per service account, to enable the service accounts to create and manage Shared VPC networks
- one optional service account key per service account

## Dependencies

- GCP Project

## Usage

```
module "service-account" {
    source = "github.com/Coalfire-CF/terraform-gcp-service-account"

    # Required 
    project_id = "your-project-id"
    names = ["service-account-name"]

    # Optional
    prefix = "sa"
    display_name = "ServiceAccount1"
    description = "description-of-service-account"
    project_roles = [
        "<your-project-id>=>roles/secretmanager.secretAccessor",
        "<your-project-id>=>roles/source.reader",
    ]
}
```
