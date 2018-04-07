# TODO

## Additional Packer Parameters
kms_key_id (string) - The ID of the KMS key to use for boot volume encryption. This only applies to the main region, other regions where the AMI will be copied will be encrypted by the default EBS KMS key.

region_kms_key_ids (map of strings) - a map of regions to copy the ami to, along with the custom kms key id to use for encryption for that region. Keys must match the regions provided in ami_regions. If you just want to encrypt using a default ID, you can stick with kms_key_id and ami_regions. If you want a region to be encrypted with that region's default key ID, you can use an empty string "" instead of a key id in this map. (e.g. "us-east-1": "") However, you cannot use default key IDs if you are using this in conjunction with snapshot_users -- in that situation you must use custom keys.

snapshot_tags (object of key/value strings) - Tags to apply to snapshot. They will override AMI tags if already applied to snapshot. This is a template engine where the SourceAMI variable is replaced with the source AMI ID and BuildRegion variable is replaced with name of the region where this is built.

snapshot_groups (array of strings) - A list of groups that have access to create volumes from the snapshot(s). By default no groups have permission to create volumes from the snapshot(s). all will make the snapshot publicly accessible.

snapshot_users (array of strings) - A list of account IDs that have access to create volumes from the snapshot(s). By default no additional users other than the user creating the AMI has permissions to create volumes from the backing snapshot(s).

## Security Enhancements

Ansible role for CIS Benchmark
Vagrantfile
Serverspec tests