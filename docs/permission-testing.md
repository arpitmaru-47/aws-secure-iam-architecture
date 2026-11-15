
# IAM Permission Testing

## Test Environment

- IAM User: `devops-user`
- IAM Group: `DevOps-Developers`
- S3 Bucket: `devops-iam-lab-2026-unique`
- Custom Policy: `DevOps-S3-Limited-Access`

## Permission Test Results

| Test | Expected Result | Observed Result |
|---|---|---|
| List S3 bucket names | Allow | Allowed after policy update |
| List lab bucket contents | Allow | Successful |
| Upload object | Allow | Successful |
| Download object | Allow | Successful |
| Delete object | Deny | Failed to delete object |
| List IAM policies | Deny | Access Denied |

## EC2 IAM Role

Role Name: `EC2-S3-Limited-Role`

Trusted Service: `ec2.amazonaws.com`

Permission Policy: `DevOps-S3-Limited-Access`

Status: Role created and trust relationship verified. Actual EC2 instance attachment and runtime access testing are pending.

## CloudTrail Verification

The following IAM management events were found in CloudTrail Event History:

- `CreateRole`
- `CreatePolicy`
- `AttachGroupPolicy`
- `AttachRolePolicy`

## Conclusion

The project demonstrates IAM group-based permission management, restricted S3 object access, an EC2 service role, and CloudTrail management-event auditing.

The developer can upload and download objects from the designated lab bucket but cannot delete objects or access IAM policy listings.

The EC2 role has been configured but still requires an actual EC2 runtime test.
