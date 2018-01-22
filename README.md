# suptree
An OS process supervisor tree loosely modeled on erlang.

The purpose is grouping collections of processes so they can be effectively started, stopped and logged as one. This
is useful for development of multiple interacting services and also other situations like multi purpose containers.


Example config:

```
restart_strategy: one_for_one
restart_intensity: 1
restart_period_seconds: 5

children:
	- name: "haproxy"
	  exec: ["haproxy", "...", "..."]

	- name: "apache"
	  exec: ["apache", "...", "..."]

  	- name: "django"
	  exec: ["gunicorn", "...", "..."]
```

Plans for the future:

- nested supervisors.
- remove supervisors over ssh.
- failover?
