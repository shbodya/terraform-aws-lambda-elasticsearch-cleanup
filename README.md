<!-- This file was automatically generated by the `build-harness`. Make all changes to `README.yaml` and run `make readme` to rebuild this file. -->
[![README Header][readme_header_img]][readme_header_link]

[![Cloud Posse][logo]](https://cpco.io/homepage)

# terraform-aws-lambda-elasticsearch-cleanup

 [![Build Status](https://travis-ci.org/cloudposse/terraform-aws-lambda-elasticsearch-cleanup.svg?branch=master)](https://travis-ci.org/cloudposse/terraform-aws-lambda-elasticsearch-cleanup) [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-aws-lambda-elasticsearch-cleanup.svg)](https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup/releases/latest) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com)


Terraform module to provision a scheduled Lambda function which will 
delete old Elasticsearch indexes using [SigV4Auth](https://docs.aws.amazon.com/AmazonS3/latest/API/sig-v4-authenticating-requests.html) authentication. The
lambda function can optionally send output to an SNS topic if the 
topic ARN is given. This module was largely inspired by 
[aws-lambda-es-cleanup](https://github.com/cloudreach/aws-lambda-es-cleanup)


---

This project is part of our comprehensive ["SweetOps"](https://cpco.io/sweetops) approach towards DevOps. 
[<img align="right" title="Share via Email" src="https://docs.cloudposse.com/images/ionicons/ios-email-outline-2.0.1-16x16-999999.svg"/>][share_email]
[<img align="right" title="Share on Google+" src="https://docs.cloudposse.com/images/ionicons/social-googleplus-outline-2.0.1-16x16-999999.svg" />][share_googleplus]
[<img align="right" title="Share on Facebook" src="https://docs.cloudposse.com/images/ionicons/social-facebook-outline-2.0.1-16x16-999999.svg" />][share_facebook]
[<img align="right" title="Share on Reddit" src="https://docs.cloudposse.com/images/ionicons/social-reddit-outline-2.0.1-16x16-999999.svg" />][share_reddit]
[<img align="right" title="Share on LinkedIn" src="https://docs.cloudposse.com/images/ionicons/social-linkedin-outline-2.0.1-16x16-999999.svg" />][share_linkedin]
[<img align="right" title="Share on Twitter" src="https://docs.cloudposse.com/images/ionicons/social-twitter-outline-2.0.1-16x16-999999.svg" />][share_twitter]


[![Terraform Open Source Modules](https://docs.cloudposse.com/images/terraform-open-source-modules.svg)][terraform_modules]



It's 100% Open Source and licensed under the [APACHE2](LICENSE).







We literally have [*hundreds of terraform modules*][terraform_modules] that are Open Source and well-maintained. Check them out! 







## Usage


**IMPORTANT:** The `master` branch is used in `source` just as an example. In your code, do not pin to `master` because there may be breaking changes between releases.
Instead pin to the release tag (e.g. `?ref=tags/x.y.z`) of one of our [latest releases](https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup/releases).


```hcl
module "elasticsearch_cleanup" {
  source               = "../"
  es_endpoint          = "${module.elasticsearch.domain_endpoint}"
  es_domain_arn        = "${module.elasticsearch.domain_arn}"
  es_security_group_id = "${module.elasticsearch.security_group_id}"
  vpc_id               = "${module.vpc.vpc_id}"
  namespace            = "example"
  stage                = "dev"
  schedule             = "rate(5 minutes)"
}
```






## Makefile Targets
```
Available targets:

  build                               Build Lambda function zip
  dependencies                        Install dependencies
  help                                Help screen
  help/all                            Display help for all targets
  help/short                          This help short screen
  lint                                Lint terraform code

```
## Module: cloudposse/terraform-aws-lambda-elasticsearch-cleanup

This module creates a scheduled Lambda function which will delete old
Elasticsearch indexes using SigV4Auth authentication. The lambda
function can optionally send output to an SNS topic if the topic ARN
is given

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| attributes | Additional attributes (e.g. `1`) | list | `<list>` | no |
| delete_after | Number of days to preserve | string | `15` | no |
| delimiter | Delimiter to be used between `namespace`, `stage`, `name` and `attributes` | string | `-` | no |
| enabled | This module will not create any resources unless enabled is set to "true" | string | `true` | no |
| es_domain_arn | The Elasticsearch domain ARN | string | - | yes |
| es_endpoint | The Elasticsearch endpoint for the Lambda function to connect to | string | - | yes |
| es_security_group_id | The Elasticsearch cluster security group ID | string | - | yes |
| index | Index/indices to process. Use a comma-separated list. Specify `all` to match every index except for `.kibana` | string | `all` | no |
| index_format | Combined with 'index' variable and is used to evaluate the index age | string | `%Y.%m.%d` | no |
| name | Solution name, e.g. 'app' or 'cluster' | string | `app` | no |
| namespace | Namespace, which could be your organization name, e.g. 'eg' or 'cp' | string | - | yes |
| python_version | The Python version to use | string | `2.7` | no |
| schedule | CloudWatch Events rule schedule using cron or rate expression | string | `cron(0 3 * * ? *)` | no |
| sns_arn | SNS ARN to pusblish alerts | string | `` | no |
| stage | Stage, e.g. 'prod', 'staging', 'dev', or 'test' | string | - | yes |
| subnet_ids | Subnet ids | list | - | yes |
| tags | Additional tags (e.g. `map('BusinessUnit','XYZ')` | map | `<map>` | no |
| timeout | Timeout for Lambda function in seconds | string | `300` | no |
| vpc_id | The VPC ID for the Lambda function | string | - | yes |

## Outputs

| Name | Description |
|------|-------------|
| security_group_id | Security Group ID of the Lambda |




## Share the Love 

Like this project? Please give it a ★ on [our GitHub](https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup)! (it helps us **a lot**) 

Are you using this project or any of our other projects? Consider [leaving a testimonial][testimonial]. =)


## Related Projects

Check out these related projects.

- [terraform-aws-vpc](https://github.com/cloudposse/terraform-aws-vpc) - Terraform Module that defines a VPC with public/private subnets across multiple AZs with Internet Gateways
- [terraform-aws-dynamic-subnets](https://github.com/cloudposse/terraform-aws-dynamic-subnets) - Terraform module for dynamic subnets provisioning.
- [terraform-aws-elasticsearch](https://github.com/cloudposse/terraform-aws-elasticsearch) - Terraform module for AWS Elasticsearch provisioning.



## Help

**Got a question?**

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup/issues), send us an [email][email] or join our [Slack Community][slack].

[![README Commercial Support][readme_commercial_support_img]][readme_commercial_support_link]

## Commercial Support

Work directly with our team of DevOps experts via email, slack, and video conferencing. 

We provide [*commercial support*][commercial_support] for all of our [Open Source][github] projects. As a *Dedicated Support* customer, you have access to our team of subject matter experts at a fraction of the cost of a full-time engineer. 

[![E-Mail](https://img.shields.io/badge/email-hello@cloudposse.com-blue.svg)][email]

- **Questions.** We'll use a Shared Slack channel between your team and ours.
- **Troubleshooting.** We'll help you triage why things aren't working.
- **Code Reviews.** We'll review your Pull Requests and provide constructive feedback.
- **Bug Fixes.** We'll rapidly work to fix any bugs in our projects.
- **Build New Terraform Modules.** We'll [develop original modules][module_development] to provision infrastructure.
- **Cloud Architecture.** We'll assist with your cloud strategy and design.
- **Implementation.** We'll provide hands-on support to implement our reference architectures. 



## Terraform Module Development

Are you interested in custom Terraform module development? Submit your inquiry using [our form][module_development] today and we'll get back to you ASAP.


## Slack Community

Join our [Open Source Community][slack] on Slack. It's **FREE** for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build totally *sweet* infrastructure.

## Newsletter

Signup for [our newsletter][newsletter] that covers everything on our technology radar.  Receive updates on what we're up to on GitHub as well as awesome new projects we discover. 

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://cpco.io/help-out) with our other projects, we would love to hear from you! Shoot us an [email][email].

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!


## Copyright

Copyright © 2017-2019 [Cloud Posse, LLC](https://cpco.io/copyright)



## License 

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 

See [LICENSE](LICENSE) for full details.

    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      https://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.









## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know by [leaving a testimonial][testimonial]!

[![Cloud Posse][logo]][website]

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We ❤️  [Open Source Software][we_love_open_source].

We offer [paid support][commercial_support] on all of our projects.  

Check out [our other projects][github], [follow us on twitter][twitter], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.



### Contributors

|  [![Josh Myers][joshmyers_avatar]][joshmyers_homepage]<br/>[Josh Myers][joshmyers_homepage] |
|---|

  [joshmyers_homepage]: https://github.com/joshmyers
  [joshmyers_avatar]: https://github.com/joshmyers.png?size=150



[![README Footer][readme_footer_img]][readme_footer_link]
[![Beacon][beacon]][website]

  [logo]: https://cloudposse.com/logo-300x69.svg
  [docs]: https://cpco.io/docs
  [website]: https://cpco.io/homepage
  [github]: https://cpco.io/github
  [jobs]: https://cpco.io/jobs
  [hire]: https://cpco.io/hire
  [slack]: https://cpco.io/slack
  [linkedin]: https://cpco.io/linkedin
  [twitter]: https://cpco.io/twitter
  [testimonial]: https://cpco.io/leave-testimonial
  [newsletter]: https://cpco.io/newsletter
  [email]: https://cpco.io/email
  [commercial_support]: https://cpco.io/commercial-support
  [we_love_open_source]: https://cpco.io/we-love-open-source
  [module_development]: https://cpco.io/module-development
  [terraform_modules]: https://cpco.io/terraform-modules
  [readme_header_img]: https://cloudposse.com/readme/header/img?repo=cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [readme_header_link]: https://cloudposse.com/readme/header/link?repo=cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [readme_footer_img]: https://cloudposse.com/readme/footer/img?repo=cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [readme_footer_link]: https://cloudposse.com/readme/footer/link?repo=cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [readme_commercial_support_img]: https://cloudposse.com/readme/commercial-support/img?repo=cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [readme_commercial_support_link]: https://cloudposse.com/readme/commercial-support/link?repo=cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [share_twitter]: https://twitter.com/intent/tweet/?text=terraform-aws-lambda-elasticsearch-cleanup&url=https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [share_linkedin]: https://www.linkedin.com/shareArticle?mini=true&title=terraform-aws-lambda-elasticsearch-cleanup&url=https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [share_reddit]: https://reddit.com/submit/?url=https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [share_facebook]: https://facebook.com/sharer/sharer.php?u=https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [share_googleplus]: https://plus.google.com/share?url=https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [share_email]: mailto:?subject=terraform-aws-lambda-elasticsearch-cleanup&body=https://github.com/cloudposse/terraform-aws-lambda-elasticsearch-cleanup
  [beacon]: https://ga-beacon.cloudposse.com/UA-76589703-4/cloudposse/terraform-aws-lambda-elasticsearch-cleanup?pixel&cs=github&cm=readme&an=terraform-aws-lambda-elasticsearch-cleanup
