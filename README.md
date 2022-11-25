# Nimbus_scripts

openstack server create --flavor n3.1c4r \
   --image 578525b1-f1e3-495d-b673-3a3b9cd32b23 \
   --network dfb2cfd9-b746-410d-ab4b-f2e7d5bafacf \
   --security-group 0ca043f3-37cd-432b-baf8-24d05b48746d \
   --key-name rstudio


# openstack instances basic commands
list of servers, status, and basic details

'''
vagrant@vagrant:~$ openstack server list
+--------------------------------------+-----------+---------+--------------------------------+---------------------------------+-----------+
| ID                                   | Name      | Status  | Networks                       | Image                           | Flavor    |
+--------------------------------------+-----------+---------+--------------------------------+---------------------------------+-----------+
| bf59dbac-b74c-482b-8a5e-7d6fcb31bf83 | elke3     | ACTIVE  | Public external=146.118.70.101 |                                 | n3.8c32r  |
| 47dabc2b-9c99-4813-8d1c-6c71fe8052bd | phil      | SHUTOFF | Public external=146.118.68.130 | Pawsey - Ubuntu 20.04 - 2021-02 | n3.8c32r  |
| 7508c549-fe31-4ea1-a54b-e264b87953bc | medicine  | SHUTOFF | Public external=146.118.69.164 | Pawsey - Ubuntu 20.04 - 2021-02 | n3.4c16r  |
| ae78d560-e81d-4688-8e4d-8c668d93c4b0 | elke2     | SHUTOFF | Public external=146.118.65.16  | Pawsey - Ubuntu 20.04 - 2021-02 | n3.16c64r |
| 2d542aec-ec7c-4a45-a007-dcf1447ea01b | elke      | SHUTOFF | Public external=146.118.67.120 | Pawsey - Ubuntu 20.04 - 2021-02 | n3.8c32r  |
| 5bc25d83-aa27-4356-9445-6f41ec39147d | bio-synth | SHUTOFF | Public external=146.118.69.42  | Pawsey - Ubuntu 20.04 - 2021-02 | n3.2c8r   |
+--------------------------------------+-----------+---------+--------------------------------+---------------------------------+-----------+
'''

# Creating Security groups and group rules

'''
vagrant@vagrant:~/rc_files$ openstack security group create --project "research-training"  burton2
+-----------------+------------------------------------------------------------------------------------------------------------------------------------+
| Field           | Value |
+-----------------+------------------------------------------------------------------------------------------------------------------------------------+
| created_at      | 2022-11-25T07:43:40Z                 |
| description     | research-training-example            |
| id              | fc3c4e1b-8263-4589-8b4d-c0ce5050b13e |
| name            | burton2                              |
| project_id      | 8752cfdee44a4b9fa7a356ebb6330584     |
| revision_number | 1                                                                                               |
| rules           | created_at='2022-11-25T07:43:40Z', direction='egress', ethertype='IPv4', id='1ac9f84c-3879-4d35-8f63-afd2e287b1fc', updated_at='2022-11-25T07:43:40Z' |
|                 | created_at='2022-11-25T07:43:40Z', direction='egress', ethertype='IPv6', id='3ebe7945-62ad-4ba0-bf2a-0373102ed762', updated_at='2022-11-25T07:43:40Z' |
| stateful        | None                                                                                                                |
| tags            | []                                                                                                                                                    |
| updated_at      | 2022-11-25T07:43:40Z                                                                                                                                  |
+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
'''
create group rule 
'''

vagrant@vagrant:~/rc_files$ openstack security group rule create --description JNR_TEST --ingress --protocol tcp --dst-port 8787 fc3c4e1b-8263-4589-8b4d-c0ce5050b13e
+-------------------+--------------------------------------+
| Field             | Value                                |
+-------------------+--------------------------------------+
| created_at        | 2022-11-25T07:45:17Z                 |
| description       | JNR_TEST                             |
| direction         | ingress                              |
| ether_type        | IPv4                                 |
| id                | 29010afd-47bb-4acc-b469-d23cd377fd01 |
| name              | None                                 |
| port_range_max    | 8787                                 |
| port_range_min    | 8787                                 |
| project_id        | 8752cfdee44a4b9fa7a356ebb6330584     |
| protocol          | tcp                                  |
| remote_group_id   | None                                 |
| remote_ip_prefix  | 0.0.0.0/0                            |
| revision_number   | 0                                    |
| security_group_id | fc3c4e1b-8263-4589-8b4d-c0ce5050b13e |
| tags              | []                                   |
| updated_at        | 2022-11-25T07:45:17Z                 |
+-------------------+--------------------------------------+
'''
verify 

'''
vagrant@vagrant:~/rc_files$ openstack security group show burton2
+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field           | Value
                                                                                           |
+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| created_at      | 2022-11-25T07:43:40Z
                                                                                           |
| description     | research-training-example
                                                                                           |
| id              | fc3c4e1b-8263-4589-8b4d-c0ce5050b13e
                                                                                           |
| name            | burton2
                                                                                           |
| project_id      | 8752cfdee44a4b9fa7a356ebb6330584
                                                                                           |
| revision_number | 2
                                                                                           |
| rules           | created_at='2022-11-25T07:43:40Z', direction='egress', ethertype='IPv4', id='1ac9f84c-3879-4d35-8f63-afd2e287b1fc', updated_at='2022-11-25T07:43:40Z'
                                                                                           |
|                 | created_at='2022-11-25T07:45:17Z', description='JNR_TEST', direction='ingress', ethertype='IPv4', id='29010afd-47bb-4acc-b469-d23cd377fd01', port_range_max='8787', port_range_min='8787', protocol='tcp', remote_ip_prefix='0.0.0.0/0', updated_at='2022-11-25T07:45:17Z' |
|                 | created_at='2022-11-25T07:43:40Z', direction='egress', ethertype='IPv6', id='3ebe7945-62ad-4ba0-bf2a-0373102ed762', updated_at='2022-11-25T07:43:40Z'
                                                                                           |
| stateful        | None
                                                                                           |
| tags            | []
                                                                                           |
| updated_at      | 2022-11-25T07:45:17Z
                                                                                           |
+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
'''
