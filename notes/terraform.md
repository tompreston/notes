# Terraform
Infrastructure as code for various cloud platforms, including AWS, GCP.

HCL HashiCorp Configuration Language

    terraform init
    terraform plan
    terraform apply

Validate:

    terraform fmt
    terraform validate

Inspect state:

    terraform show

State is stored in the local file terraform.tfstate, or on a remote backend. For remote backend, you
will need to configure credentials in the web interface.
