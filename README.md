aws-sg
=============

Manages security groups at Amazon Web Services

Requirements
------------
- AWS account and credentials



## Role Variables


##### List of Variables

    ---
    sg_name: required
    sg_description: required
    sg_vpc_id: optional
    sg_region: "ap-southeast-2"
    sg_rules: optional
    sg_state: optional

##### Example of Variables file
    ---
    sg_list:
      - sg_name: "KubernetesSG"
        sg_description: "Kubernetes Segurity group"
        sg_vpc_id: "vpc-4f3b892a"
        sg_region: "ap-southeast-2"
        sg_state: present
        sg_rules:
          - proto: tcp
            from_port: 22
            to_port: 22
            cidr_ip: 12.34.56.78/24
          - proto: tcp
            from_port: 22
            to_port: 22
            cidr_ip: 10.1.0.0/16
          - proto: tcp
            from_port: 80
            to_port: 80
            cidr_ip: 10.1.0.0/16
          # - proto: all
          #   group_name: "KubernetesSG"
      - sg_name: "Sandbox SG"
        sg_description: "Sandbox Segurity group"
        sg_vpc_id: "vpc-4f3b892a"
        sg_region: 'ap-southeast-2'
        sg_state: present
        sg_rules:
          - proto: tcp
            from_port: 22
            to_port: 22
            cidr_ip: 10.100.0.0/16
          - proto: tcp
            from_port: 80
            to_port: 80
            cidr_ip: 10.100.0.0/16




Example Playbook
----------------

##### Simple

    ---
    - hosts: local
      connection: local
      sudo: no
      gather_facts: yes

      roles:
         - roles/marcelocorreia.aws-sg

      vars_files:
        - /path/sg.yml


License
-------

MIT

Author Information
------------------
Some useful stuff at:
  - [https://github.com/marcelocorreia](https://github.com/marcelocorreia)
  - [https://galaxy.ansible.com/list#/users/15516](https://galaxy.ansible.com/list#/users/15516)
  - [https://hub.docker.com/u/marcelocorreia/](https://hub.docker.com/u/marcelocorreia/)
  - Any issues, pull-request are welcome
