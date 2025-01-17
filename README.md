# cloudfront-security-groups
cloudfront-security-groups provisions new security groups for allowing ingress traffic over ports 80/tcp and 443/tcp from all global and applicable regional Amazon CloudFront published IP address ranges. The security groups are updated automatically any time the published IP address ranges (https://ip-ranges.amazonaws.com/ip-ranges.json) are updated.

### Prerequisite:
Make sure to open an AWS service quota request to increase the size of rules allowed on Security Groups. Cloudfront has more IPs to add to the security groups than the default allowance. AWS usually allows you to request up to 200 rules without issue.

### Example usage:
Create a Lamba function and related security groups to permit http and https traffic 
```
module "cloudfront-security-groups" {
    source               = "./modules/cloudfront-security-groups"

    aws_region           = "us-east-1"
    ec2_sg_name_global   = "cf_global_g"
    ec2_sg_name_regional = "cf_global_r"
    vpc_id               = "vpc-a30725da"
}
```
