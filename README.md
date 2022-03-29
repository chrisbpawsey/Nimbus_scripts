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
