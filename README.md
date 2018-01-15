Reproduces issue https://github.com/rvm/rvm1-ansible/issues/163

1. `vagrant up`
2. `ansible-galaxy install -r requirements.yml`
3. `ansible-playbook --inventory-file=inventory.yml playbook.yml`

It prints: 


```
➜  rvm1-ruby-version ansible-playbook --inventory-file=inventory.yml playbook.yml
[DEPRECATION WARNING]: The use of 'include' for tasks has been deprecated. Use 'import_tasks' for static inclusions or 'include_tasks' for dynamic inclusions. This feature will be removed in a future release. Deprecation warnings
can be disabled by setting deprecation_warnings=False in ansible.cfg.
[DEPRECATION WARNING]: include is kept for backwards compatibility but usage is discouraged. The module documentation details page may explain more about this rationale.. This feature will be removed in a future release. Deprecation
warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.

PLAY [app] ******************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************************************************************************
ok: [127.0.0.1]

TASK [rvm1_default_ruby_version before using rvm1 role] *********************************************************************************************************************************************************************************
ok: [127.0.0.1] => {
   "msg": "ruby-2.1.1"
}

PLAY [app] ******************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************************************************************************
ok: [127.0.0.1]

( ... ommited rvm_io.ruby output ... )

TASK [my_role : rvm1_default_ruby_version in my_role] ***********************************************************************************************************************************************************************************
ok: [127.0.0.1] => {
   "msg": "ruby-2.3.5"
}

PLAY [app] ******************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************************************************************************
ok: [127.0.0.1]

TASK [rvm1_default_ruby_version after using rvm1 role] **********************************************************************************************************************************************************************************
ok: [127.0.0.1] => {
   "msg": "ruby-2.1.1"
}

PLAY RECAP ******************************************************************************************************************************************************************************************************************************
127.0.0.1                  : ok=18   changed=6    unreachable=0    failed=0
```
