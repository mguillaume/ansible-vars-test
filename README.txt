Ansible version: 1.7.2


Test 1 (group_vars, static group):

localhost is in the test group
Command: ansible-playbook -i hosts-static test-dynamic.yml -v

OK: myvar = "group_test"



Test 2 (group_vars, dynamic group):

localhost is added in the test group with add_host
Command: ansible-playbook -i hosts-dynamic test-dynamic.yml -v

KO: myvar does not change from "group_all"



Test 3 (group_vars + roles vars):

localhost is in the test group
test role is main, with depends on dep
Command: ansible-playbook -i hosts-static test-roles.yml -v

KO?: role variable takes precedence over group_vars
OK: main role variable takes precendence over dependent role variable

