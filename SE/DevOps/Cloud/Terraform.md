Infrastructure as Code
- Đa dạng cloud provider: Alibaba Cloud, AWS, Azure
- Quản lý hệ thống bằng code tự động hóa triển khai hạ tầng
- Sử dụng ngôn ngữ HCL (HashiCorp Configuration Language)
![[terraform.png]]
```c
terraform --version 
terraform --help // list commands 
terraform init //
```
### Workflow - 3 stages
- **Write**: Define resources
- **Plan**: Terraform creates an execution plan describing the infrastructure it will create, update, or destroy based on the existing infrastructure and your configuration
- **Apply:** On approval, Terraform performs the proposed operations in the correct order, respecting any resource dependencies. For example, if you update the properties of a VPC and change the number of virtual machines in that VPC, Terraform will recreate the VPC before scaling the virtual machines.

To deploy infrastructure with Terraform:
- **Scope** - Identify the infrastructure for your project.
- **Author** - Write the configuration for your infrastructure.
- **Initialize** - Install the plugins Terraform needs to manage the infrastructure.
- **Plan** - Preview the changes Terraform will make to match your configuration.
- **Apply** - Make the planned changes.

[Create Google Cloud Functions using Terraform | 1st gen | 2nd gen](https://www.youtube.com/watch?v=I81UlLNLdb0)