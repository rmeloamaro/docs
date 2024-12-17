# AWS - Identify Unused VPCs

## Overview

This job is designed to identify unused Virtual Private Clouds (VPCs) in a specified AWS region. It helps in cost management and resource optimization by highlighting VPCs that are not associated with any active AWS resources and may be candidates for deletion.

## Functionality

The job performs the following tasks:

1. Retrieves a list of all VPCs in the specified AWS region.
2. Identifies the default VPC and excludes it from further processing.
3. Checks each non-default VPC for associations with various AWS resources, including:
   - EC2 instances
   - RDS instances
   - Classic Load Balancers (ELB)
   - Application and Network Load Balancers (ALB/NLB)
   - NAT Gateways
   - VPN Connections
   - Transit Gateway attachments
4. Compiles a list of VPCs that are not associated with any of the above resources.
5. Outputs a list of VPCs that can potentially be deleted.

## Setup

### Prerequisites

- Turn on "[Runner as Node](/administration/runner/runner-management/node-dispatch.html#runner-as-a-node)" setting on your Runner.  
  - This requires version 5.8.0 or higher.  Adjustments to Node tab may be required for earlier versions.
- AWS CLI installed on the Enterprise Runner node.
- Appropriate AWS IAM permissions (see below).

### Job Configuration

1. **Node Filter**: The job is configured to run on nodes tagged with "RUNNER".
2. **Options**:
   - `region`: AWS Region (required, uses aws-regions-job-options plugin)
   - `always-show-results`: Show results even after an error (true/false)
3. **Execution**: The job runs a bash script that utilizes AWS CLI commands.

## AWS IAM Permissions

The IAM role or user executing this job needs the following permissions:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeVpcs",
                "ec2:DescribeInstances",
                "ec2:DescribeNatGateways",
                "ec2:DescribeVpnConnections",
                "ec2:DescribeTransitGatewayVpcAttachments",
                "rds:DescribeDBInstances",
                "elasticloadbalancing:DescribeLoadBalancers"
            ],
            "Resource": "*"
        }
    ]
}
```

These permissions allow the script to describe various AWS resources across different services to determine VPC usage.

## Running the Job
1. Select the job in the Cost Management / AWS folder.
2. Choose the target AWS region from the dropdown.
3. Set the always-show-results option as needed.
4. Execute the job.

## Output

The job will provide:

- A list of all VPCs in the region.
- Information about associated resources for each VPC.
- A list of VPCs that appear to be unused and can potentially be deleted.

## Important Notes

- The job does not automatically delete any VPCs; it only identifies potential candidates for deletion.
- Always verify the results manually before deleting any VPC.
- The default VPC is automatically excluded from the list of deletable VPCs.
- If errors occur during execution, the job can be configured to show partial results.

## Troubleshooting
- Turn on "[Runner as Node](/administration/runner/runner-management/node-dispatch.html#runner-as-a-node)" setting on your Runner.  This requires version 5.8.0 or higher.  Adjustments to Node tab may be required for earlier versions.
- Ensure the Enterprise Runner node has the AWS CLI properly configured.  There are helper jobs in the _Getting Started_ folder of the project.
- Verify that the IAM role or user has the necessary permissions. (See above)
- Check execution logs for any execution errors.


## Security Considerations
- Follow the principle of least privilege when assigning IAM permissions.
- Regularly review and update the permissions as needed.
- Ensure that sensitive information, like AWS credentials, are securely managed.