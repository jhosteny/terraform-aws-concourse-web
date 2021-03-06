<!-- markdownlint-disable -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | ~> 0.14.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | ~> 3.32 |
| <a name="requirement_external"></a> [external](#requirement\_external) | ~> 2.1 |
| <a name="requirement_http"></a> [http](#requirement\_http) | ~> 2.0 |
| <a name="requirement_local"></a> [local](#requirement\_local) | ~> 2.0 |
| <a name="requirement_template"></a> [template](#requirement\_template) | ~> 2.2 |
| <a name="requirement_utils"></a> [utils](#requirement\_utils) | ~> 0.3 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | ~> 3.32 |
| <a name="provider_random"></a> [random](#provider\_random) | n/a |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_alb"></a> [alb](#module\_alb) | cloudposse/alb/aws | 0.33.0 |
| <a name="module_create_db_container_definition"></a> [create\_db\_container\_definition](#module\_create\_db\_container\_definition) | cloudposse/ecs-container-definition/aws | 0.56.0 |
| <a name="module_download_keys_container_definition"></a> [download\_keys\_container\_definition](#module\_download\_keys\_container\_definition) | cloudposse/ecs-container-definition/aws | 0.56.0 |
| <a name="module_nlb"></a> [nlb](#module\_nlb) | cloudposse/nlb/aws | 0.8.0 |
| <a name="module_this"></a> [this](#module\_this) | cloudposse/label/null | 0.24.1 |
| <a name="module_web"></a> [web](#module\_web) | cloudposse/ecs-web-app/aws | 0.61.0 |

## Resources

| Name | Type |
|------|------|
| [aws_ecs_cluster.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ecs_cluster) | resource |
| [aws_iam_policy.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_role_policy_attachment.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_security_group_rule.tsa_http_health_check_in](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule) | resource |
| [aws_sns_topic.sns_topic](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/sns_topic) | resource |
| [random_password.default](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [aws_iam_policy_document.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_vpc.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/vpc) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_additional_tag_map"></a> [additional\_tag\_map](#input\_additional\_tag\_map) | Additional tags for appending to tags\_as\_list\_of\_maps. Not added to `tags`. | `map(string)` | `{}` | no |
| <a name="input_attributes"></a> [attributes](#input\_attributes) | Additional attributes (e.g. `1`) | `list(string)` | `[]` | no |
| <a name="input_autoscaling_dimension"></a> [autoscaling\_dimension](#input\_autoscaling\_dimension) | Dimension to autoscale on (valid options: cpu, memory) | `string` | `"cpu"` | no |
| <a name="input_autoscaling_enabled"></a> [autoscaling\_enabled](#input\_autoscaling\_enabled) | A boolean to enable/disable Autoscaling policy for ECS Service | `bool` | `false` | no |
| <a name="input_certificate_arn"></a> [certificate\_arn](#input\_certificate\_arn) | ARN of the ALB (HTTPS) certificate | `string` | n/a | yes |
| <a name="input_chamber_kms_key_arn"></a> [chamber\_kms\_key\_arn](#input\_chamber\_kms\_key\_arn) | ARN of the chamber KMS key | `string` | `""` | no |
| <a name="input_concourse_db_name"></a> [concourse\_db\_name](#input\_concourse\_db\_name) | Concourse PostgreSQL database name | `string` | `"concourse"` | no |
| <a name="input_concourse_db_password"></a> [concourse\_db\_password](#input\_concourse\_db\_password) | Password for the Concourse database user | `string` | `""` | no |
| <a name="input_concourse_db_username"></a> [concourse\_db\_username](#input\_concourse\_db\_username) | Username for the Concourse database | `string` | `"concourse"` | no |
| <a name="input_concourse_docker_image"></a> [concourse\_docker\_image](#input\_concourse\_docker\_image) | Concourse docker image | `string` | `"concourse/concourse"` | no |
| <a name="input_concourse_github_auth_client_id"></a> [concourse\_github\_auth\_client\_id](#input\_concourse\_github\_auth\_client\_id) | Github client id | `string` | `null` | no |
| <a name="input_concourse_github_auth_client_secret"></a> [concourse\_github\_auth\_client\_secret](#input\_concourse\_github\_auth\_client\_secret) | Github client secret | `string` | `null` | no |
| <a name="input_concourse_main_team_github_org"></a> [concourse\_main\_team\_github\_org](#input\_concourse\_main\_team\_github\_org) | Github team that can login | `string` | `null` | no |
| <a name="input_concourse_main_team_github_team"></a> [concourse\_main\_team\_github\_team](#input\_concourse\_main\_team\_github\_team) | Github team that can login | `string` | `null` | no |
| <a name="input_concourse_version"></a> [concourse\_version](#input\_concourse\_version) | Concourse version to use | `string` | `"5.8.0"` | no |
| <a name="input_container_cpu"></a> [container\_cpu](#input\_container\_cpu) | The vCPU setting to control cpu limits of container | `number` | `256` | no |
| <a name="input_container_memory"></a> [container\_memory](#input\_container\_memory) | The amount of RAM to allow container to use in MB | `number` | `512` | no |
| <a name="input_container_memory_reservation"></a> [container\_memory\_reservation](#input\_container\_memory\_reservation) | The amount of RAM (Soft Limit) to allow container to use in MB. This value must be less than `container_memory` if set | `number` | `128` | no |
| <a name="input_context"></a> [context](#input\_context) | Single object for setting entire context at once.<br>See description of individual variables for details.<br>Leave string and numeric variables as `null` to use default value.<br>Individual variable settings (non-null) override settings in context object,<br>except for attributes, tags, and additional\_tag\_map, which are merged. | <pre>object({<br>    enabled             = bool<br>    namespace           = string<br>    environment         = string<br>    stage               = string<br>    name                = string<br>    delimiter           = string<br>    attributes          = list(string)<br>    tags                = map(string)<br>    additional_tag_map  = map(string)<br>    regex_replace_chars = string<br>    label_order         = list(string)<br>    id_length_limit     = number<br>  })</pre> | <pre>{<br>  "additional_tag_map": {},<br>  "attributes": [],<br>  "delimiter": null,<br>  "enabled": true,<br>  "environment": null,<br>  "id_length_limit": null,<br>  "label_order": [],<br>  "name": null,<br>  "namespace": null,<br>  "regex_replace_chars": null,<br>  "stage": null,<br>  "tags": {}<br>}</pre> | no |
| <a name="input_db_admin_password"></a> [db\_admin\_password](#input\_db\_admin\_password) | Admin password of the PostgreSQL database server | `string` | n/a | yes |
| <a name="input_db_admin_username"></a> [db\_admin\_username](#input\_db\_admin\_username) | Admin user of the PostgreSQL database server | `string` | n/a | yes |
| <a name="input_db_hostname"></a> [db\_hostname](#input\_db\_hostname) | PostgreSQL server hostname or IP | `string` | n/a | yes |
| <a name="input_db_name"></a> [db\_name](#input\_db\_name) | Default PostgreSQL database | `string` | `"postgres"` | no |
| <a name="input_db_port"></a> [db\_port](#input\_db\_port) | Port of the PostgreSQL server | `string` | `"5432"` | no |
| <a name="input_db_security_group_id"></a> [db\_security\_group\_id](#input\_db\_security\_group\_id) | Database security group ID | `string` | n/a | yes |
| <a name="input_db_version"></a> [db\_version](#input\_db\_version) | PostgreSQL engine version used in the Concourse database server | `string` | n/a | yes |
| <a name="input_delimiter"></a> [delimiter](#input\_delimiter) | Delimiter to be used between `namespace`, `environment`, `stage`, `name` and `attributes`.<br>Defaults to `-` (hyphen). Set to `""` to use no delimiter at all. | `string` | `null` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | Set to false to prevent the module from creating any resources | `bool` | `null` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | Environment, e.g. 'uw2', 'us-west-2', OR 'prod', 'staging', 'dev', 'UAT' | `string` | `null` | no |
| <a name="input_external_url_https"></a> [external\_url\_https](#input\_external\_url\_https) | Concourse external URL (fully qualified, e.g. `https://concourse.prod.acme.co`) | `string` | n/a | yes |
| <a name="input_id_length_limit"></a> [id\_length\_limit](#input\_id\_length\_limit) | Limit `id` to this many characters.<br>Set to `0` for unlimited length.<br>Set to `null` for default, which is `0`.<br>Does not affect `id_full`. | `number` | `null` | no |
| <a name="input_ingress_cidr_blocks_https"></a> [ingress\_cidr\_blocks\_https](#input\_ingress\_cidr\_blocks\_https) | List of CIDR blocks allowed to access Concourse over HTTPS | `list(string)` | <pre>[<br>  "0.0.0.0/0"<br>]</pre> | no |
| <a name="input_keys_bucket_arn"></a> [keys\_bucket\_arn](#input\_keys\_bucket\_arn) | ARN of the bucket holding the keys | `string` | n/a | yes |
| <a name="input_keys_bucket_id"></a> [keys\_bucket\_id](#input\_keys\_bucket\_id) | ID of the bucket holding the keys | `string` | n/a | yes |
| <a name="input_label_order"></a> [label\_order](#input\_label\_order) | The naming order of the id output and Name tag.<br>Defaults to ["namespace", "environment", "stage", "name", "attributes"].<br>You can omit any of the 5 elements, but at least one must be present. | `list(string)` | `null` | no |
| <a name="input_name"></a> [name](#input\_name) | Solution name, e.g. 'app' or 'jenkins' | `string` | `null` | no |
| <a name="input_namespace"></a> [namespace](#input\_namespace) | Namespace, which could be your organization name or abbreviation, e.g. 'eg' or 'cp' | `string` | `null` | no |
| <a name="input_private_subnet_ids"></a> [private\_subnet\_ids](#input\_private\_subnet\_ids) | List of private VPC subnet IDs | `list(string)` | n/a | yes |
| <a name="input_public_subnet_ids"></a> [public\_subnet\_ids](#input\_public\_subnet\_ids) | List of public VPC subnet IDs | `list(string)` | n/a | yes |
| <a name="input_regex_replace_chars"></a> [regex\_replace\_chars](#input\_regex\_replace\_chars) | Regex to replace chars with empty string in `namespace`, `environment`, `stage` and `name`.<br>If not set, `"/[^a-zA-Z0-9-]/"` is used to remove all characters other than hyphens, letters and digits. | `string` | `null` | no |
| <a name="input_region"></a> [region](#input\_region) | AWS Region for deployment | `string` | n/a | yes |
| <a name="input_stage"></a> [stage](#input\_stage) | Stage, e.g. 'prod', 'staging', 'dev', OR 'source', 'build', 'test', 'deploy', 'release' | `string` | `null` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | Additional tags (e.g. `map('BusinessUnit','XYZ')` | `map(string)` | `{}` | no |
| <a name="input_task_cpu"></a> [task\_cpu](#input\_task\_cpu) | The number of CPU units used by the task | `number` | `null` | no |
| <a name="input_task_memory"></a> [task\_memory](#input\_task\_memory) | The amount of memory (in MiB) used by the task | `number` | `null` | no |
| <a name="input_tsa_certificate_arn"></a> [tsa\_certificate\_arn](#input\_tsa\_certificate\_arn) | ARN of the NLB certificate | `string` | n/a | yes |
| <a name="input_vpc_id"></a> [vpc\_id](#input\_vpc\_id) | VPC ID for deployment | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_alb_dns_name"></a> [alb\_dns\_name](#output\_alb\_dns\_name) | ALB DNS name |
| <a name="output_ecs_service_security_group_id"></a> [ecs\_service\_security\_group\_id](#output\_ecs\_service\_security\_group\_id) | Security Group ID of the ECS task |
| <a name="output_ecs_task_role_name"></a> [ecs\_task\_role\_name](#output\_ecs\_task\_role\_name) | Name of the ECS task role |
| <a name="output_nlb_dns_name"></a> [nlb\_dns\_name](#output\_nlb\_dns\_name) | NLB DNS name |
<!-- markdownlint-restore -->
