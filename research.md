# Reference for Ansible Callback Modules #

This is an attempt to demystify the callback modules so if you wish to make a new callback module or a change to an existing one.
When I started with callback modules I was frustrated with the lack of documentation in regards to what the methods do, and how they affect the output of ansible, so this is an attempt to clarify that for those who wish to change callback modules.


## Methods for Ansible Callback class ##
The following code snippet returns all of the methods of the Callback Class
These call also be found in __init__.py in the callback folder
```
from ansible.plugins.callback import CallbackBase
for name,obj in  CallbackBase.__dict__.iteritems() :
    print '%-25s  -->  %r' % (name, obj)
```

## Methods and initial state ##
Without a callback module this is is the initial state of each method, and the primary relevant actions of those methods.

### Runner methods ###								
|	v2 items	|	v1 items	|	initial defaults v2	|	initial defaults v1	|
|	-------------	|	-------------	|	-------------	|	-------------	|
|	v2_runner_item_on_failed	|		|	pass	|		|
|	v2_runner_item_on_ok	|		|	pass	|		|
|	v2_runner_item_on_skipped	|		|	pass	|		|
|	v2_runner_on_async_failed	|	runner_on_async_failed	|	Sets var host, job_id	|	pass	|
|	v2_runner_on_async_ok	|	runner_on_async_ok	|	Sets var host, job_id	|	pass	|
|	v2_runner_on_async_poll	|	runner_on_async_poll	|	Sets var host, job_id, clock	|	pass	|
|	v2_runner_on_failed	|	runner_on_failed	|	Sets var host	|	pass	|
|	v2_runner_on_file_diff	|		|	pass	|		|
|	v2_runner_on_no_hosts	|	runner_on_no_hosts	|	pass	|	pass	|
|	v2_runner_on_ok	|	runner_on_ok	|	Sets var host	|	pass	|
|	v2_runner_on_skipped	|	runner_on_skipped	|	if showing skipped show skipped host	|	pass	|
|	v2_runner_on_unreachable	|	runner_on_unreachable	|	Sets var host	|	pass	|
|	v2_runner_retry	|		|	pass	|		|

### Playbooks methods ###								
|	v2 items	|	v1 items	|	initial defaults v2	|	initial defaults v1	|
|	-------------	|	-------------	|	-------------	|	-------------	|
|	v2_playbook_on_cleanup_task_start	|		|	pass	|		|
|	v2_playbook_on_handler_task_start	|		|	pass	|		|
|	v2_playbook_on_import_for_host	|	playbook_on_import_for_host	|	Sets var host	|	pass	|
|	v2_playbook_on_include	|		|	pass	|		|
|	v2_playbook_on_no_hosts_matched	|	playbook_on_no_hosts_matched	|	pass	|	pass	|
|	v2_playbook_on_no_hosts_remaining	|	playbook_on_no_hosts_remaining	|	pass	|	pass	|
|	v2_playbook_on_not_import_for_host	|	playbook_on_not_import_for_host	|	Sets var host	|	pass	|
|	v2_playbook_on_notify	|	playbook_on_notify	|	Sets var host	|	pass	|
|	v2_playbook_on_play_start	|	playbook_on_play_start	|	pass	|	pass	|
|	v2_playbook_on_setup	|	playbook_on_setup	|	pass	|	pass	|
|	v2_playbook_on_start	|	playbook_on_start	|	pass	|	pass	|
|	v2_playbook_on_stats	|	playbook_on_stats	|	pass	|	pass	|
|	v2_playbook_on_task_start	|	playbook_on_task_start	|	pass	|	pass	|
|	v2_playbook_on_vars_prompt	|	playbook_on_vars_prompt	|	pass	|	pass	|

### Misc methods ###								
|	v2 items	|	v1 items	|	initial defaults v2	|	initial defaults v1	|
|	-------------	|	-------------	|	-------------	|	-------------	|
|		|	\__init\__	|		|	sets options, display, etc	|
|		|	_clean_results	|		|	removes data from results for display	|
|		|	_dump_results	|		|	indents results, Removes base keys, exepction. Removes invocation and diff in result when less than level 3 verbosity. Returns json	|
|		|	_get_diff	|		|	Returns differences	|
|		|	_get_item	|		|	Sets var item	|
|		|	_handle_exception	|		|	Displays exeption occured, and if Verbosity 3 shows traceback	|
|		|	_handle_warnings	|		|	Displays 'warnings and depreciations	|
|		|	_process_items	|		|	Del items, now handeled by individual callbacks	|
|	v2_on_any	|	on_any	|	pass	|	pass	|
|	v2_on_file_diff	|	on_file_diff	|	Sets var host	|	pass	|
|		|	set_options	|		|	Sets options, default is none	|
|		|	set_play_context	|		|	pass	|
|	Within default Callback module only	|	_print_task_banner	|		|		|

## Default Callback Module ##
The methods called in the default callback module and what they do.

### Runner methods ###								
|	v2 items	|	Default callback Plugin	|					
|	-------------	|	-------------	|					
|	v2_runner_item_on_failed	|	Displays "failed: [host_name] result" Dump results	|					
|	v2_runner_item_on_ok	|	Displays "Ok" or "Changed"	|					
|	v2_runner_item_on_skipped	|	Displays "skipping: [host_name]"	|					
|	v2_runner_on_async_failed	|		|					
|	v2_runner_on_async_ok	|		|					
|	v2_runner_on_async_poll	|		|					
|	v2_runner_on_failed	|	Displays "fatal: [%s -> %s]: FAILED! => %s" or "...ignoring"	|					
|	v2_runner_on_file_diff	|		|					
|	v2_runner_on_no_hosts	|		|					
|	v2_runner_on_ok	|	Displays "changed: [host_name]" or "ok: [host_name]"	|					
|	v2_runner_on_skipped	|		|					
|	v2_runner_on_unreachable	|	Displays "fatal: [%s -> %s]: UNREACHABLE! => %s"	|					
|	v2_runner_retry	|	Displays "FAILED - RETRYING" task and retries left	|					

### Playbooks methods ###								
|	v2 items	|	Default callback Plugin	|					
|	-------------	|	-------------	|					
|	v2_playbook_on_cleanup_task_start	|	Display "CLEANUP TASK [task_name]"	|					
|	v2_playbook_on_handler_task_start	|	Display "RUNNING HANDLER [handler_task_name]"	|					
|	v2_playbook_on_import_for_host	|		|					
|	v2_playbook_on_include	|	Display 'included: %s for %s'	|					
|	v2_playbook_on_no_hosts_matched	|	Display "skipping: no hosts matched"	|					
|	v2_playbook_on_no_hosts_remaining	|	Display "NO MORE HOSTS LEFT"	|					
|	v2_playbook_on_not_import_for_host	|		|					
|	v2_playbook_on_notify	|		|					
|	v2_playbook_on_play_start	|	Displays play name	|					
|	v2_playbook_on_setup	|	Displays "skipping: [host_name] => (item=%s) "	|					
|	v2_playbook_on_start	|	Displays playbook and verbosity level	|					
|	v2_playbook_on_stats	|	Displays "PLAY RECAP" and host summary	|					
|	v2_playbook_on_task_start	|	Displays the task via print task banner	|					
|	v2_playbook_on_vars_prompt	|		|					

### Misc methods ###								
|	v2 items	|	Default callback Plugin	|					
|	-------------	|	-------------	|					
|	\__init\__	|	Sets vars self._play, self._last_task_banner to None	|					
|	v2_on_file_diff	|	shows diff on file changed	|					
|	Within default Callback module only	|	Displays task	|					
