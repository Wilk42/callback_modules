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

Here are the current methods for the CallbackBase

```
    __module__                 -->  'ansible.plugins.callback'
    v2_runner_item_on_skipped  -->  <function v2_runner_item_on_skipped at 0x7efc76730aa0>
    runner_on_async_poll       -->  <function runner_on_async_poll at 0x7efc76731668>
    v2_playbook_on_stats       -->  <function v2_playbook_on_stats at 0x7efc76730848>
    v2_playbook_on_start       -->  <function v2_playbook_on_start at 0x7efc767302a8>
    v2_runner_on_unreachable   -->  <function v2_runner_on_unreachable at 0x7efc76731f50>
    on_file_diff               -->  <function on_file_diff at 0x7efc76731cf8>
    on_any                     -->  <function on_any at 0x7efc76731398>
    playbook_on_not_import_for_host  -->  <function playbook_on_not_import_for_host at 0x7efc76731b90>
    playbook_on_notify         -->  <function playbook_on_notify at 0x7efc76731848>
    runner_on_no_hosts         -->  <function runner_on_no_hosts at 0x7efc767315f0>
    v2_playbook_on_include     -->  <function v2_playbook_on_include at 0x7efc76730938>
    v2_runner_on_async_failed  -->  <function v2_runner_on_async_failed at 0x7efc767301b8>
    runner_on_skipped          -->  <function runner_on_skipped at 0x7efc76731500>
    playbook_on_no_hosts_remaining  -->  <function playbook_on_no_hosts_remaining at 0x7efc76731938>
    v2_on_file_diff            -->  <function v2_on_file_diff at 0x7efc767308c0>
    v2_playbook_on_setup       -->  <function v2_playbook_on_setup at 0x7efc76730668>
    _abc_negative_cache_version  -->  173
    playbook_on_import_for_host  -->  <function playbook_on_import_for_host at 0x7efc76731b18>
    _dump_results              -->  <function _dump_results at 0x7efc76733f50>
    v2_runner_on_async_ok      -->  <function v2_runner_on_async_ok at 0x7efc76730140>
    __abstractmethods__        -->  frozenset([])
    _process_items             -->  <function _process_items at 0x7efc76731230>
    v2_playbook_on_no_hosts_matched  -->  <function v2_playbook_on_no_hosts_matched at 0x7efc76730398>
    _clean_results             -->  <function _clean_results at 0x7efc767312a8>
    v2_playbook_on_handler_task_start  -->  <function v2_playbook_on_handler_task_start at 0x7efc76730578>
    runner_on_failed           -->  <function runner_on_failed at 0x7efc76731410>
    playbook_on_play_start     -->  <function playbook_on_play_start at 0x7efc76731c08>
    _copy_result               -->  <function deepcopy at 0x7efc77775ed8>
    runner_on_async_failed     -->  <function runner_on_async_failed at 0x7efc76731758>
    playbook_on_setup          -->  <function playbook_on_setup at 0x7efc76731aa0>
    __doc__                    -->  '\n    This is a base ansible callback class that does nothing. New callbacks should\n    use this class as a base and override any callback methods they wish to execute\n    custom actions.\n    '
    v2_runner_on_no_hosts      -->  <function v2_runner_on_no_hosts at 0x7efc76730050>
    v2_playbook_on_play_start  -->  <function v2_playbook_on_play_start at 0x7efc767307d0>
    _abc_cache                 -->  <_weakrefset.WeakSet object at 0x7efc765640d0>
    playbook_on_no_hosts_matched  -->  <function playbook_on_no_hosts_matched at 0x7efc767318c0>
    runner_on_async_ok         -->  <function runner_on_async_ok at 0x7efc767316e0>
    playbook_on_start          -->  <function playbook_on_start at 0x7efc767317d0>
    runner_on_unreachable      -->  <function runner_on_unreachable at 0x7efc76731578>
    v2_playbook_on_no_hosts_remaining  -->  <function v2_playbook_on_no_hosts_remaining at 0x7efc76730410>
    v2_runner_on_ok            -->  <function v2_runner_on_ok at 0x7efc76731e60>
    v2_runner_on_async_poll    -->  <function v2_runner_on_async_poll at 0x7efc767300c8>
    v2_runner_on_skipped       -->  <function v2_runner_on_skipped at 0x7efc76731ed8>
    _abc_negative_cache        -->  <_weakrefset.WeakSet object at 0x7efc76564110>
    _get_item                  -->  <function _get_item at 0x7efc767311b8>
    v2_playbook_on_vars_prompt  -->  <function v2_playbook_on_vars_prompt at 0x7efc767305f0>
    v2_runner_on_failed        -->  <function v2_runner_on_failed at 0x7efc76731de8>
    v2_playbook_on_import_for_host  -->  <function v2_playbook_on_import_for_host at 0x7efc767306e0>
    v2_runner_on_file_diff     -->  <function v2_runner_on_file_diff at 0x7efc76730230>
    v2_playbook_on_cleanup_task_start  -->  <function v2_playbook_on_cleanup_task_start at 0x7efc76730500>
    set_options                -->  <function set_options at 0x7efc76733ed8>
    v2_runner_retry            -->  <function v2_runner_retry at 0x7efc76730b18>
    v2_on_any                  -->  <function v2_on_any at 0x7efc76731d70>
    runner_on_ok               -->  <function runner_on_ok at 0x7efc76731488>
    v2_runner_item_on_ok       -->  <function v2_runner_item_on_ok at 0x7efc767309b0>
    playbook_on_vars_prompt    -->  <function playbook_on_vars_prompt at 0x7efc76731a28>
    v2_playbook_on_notify      -->  <function v2_playbook_on_notify at 0x7efc76730320>
    v2_runner_item_on_failed   -->  <function v2_runner_item_on_failed at 0x7efc76730a28>
    playbook_on_stats          -->  <function playbook_on_stats at 0x7efc76731c80>
    _handle_warnings           -->  <function _handle_warnings at 0x7efc76731050>
    _get_diff                  -->  <function _get_diff at 0x7efc76731140>
    _handle_exception          -->  <function _handle_exception at 0x7efc767310c8>
    __init__                   -->  <function __init__ at 0x7efc76733e60>
    v2_playbook_on_not_import_for_host  -->  <function v2_playbook_on_not_import_for_host at 0x7efc76730758>
    playbook_on_task_start     -->  <function playbook_on_task_start at 0x7efc767319b0>
    _abc_registry              -->  <_weakrefset.WeakSet object at 0x7efc7655cfd0>
    v2_playbook_on_task_start  -->  <function v2_playbook_on_task_start at 0x7efc76730488>
    set_play_context           -->  <function set_play_context at 0x7efc76731320>
```
## Runner methods ##										
|	v2 items	|	v1 items	|	initial defaults v2	|	initial defaults v1	|	Default callback Plugin	|
|	-------------	|	-------------	|	-------------	|	-------------	|	-------------	|
|	v2_runner_item_on_failed	|		|	pass	|		|	Displays "failed: [host_name] result" Dump results	|
|	v2_runner_item_on_ok	|		|	pass	|		|	Displays "Ok" or "Changed"	|
|	v2_runner_item_on_skipped	|		|	pass	|		|	Displays "skipping: [host_name]"	|
|	v2_runner_on_async_failed	|	runner_on_async_failed	|	Sets var host, job_id	|	pass	|		|
|	v2_runner_on_async_ok	|	runner_on_async_ok	|	Sets var host, job_id	|	pass	|		|
|	v2_runner_on_async_poll	|	runner_on_async_poll	|	Sets var host, job_id, clock	|	pass	|		|
|	v2_runner_on_failed	|	runner_on_failed	|	Sets var host	|	pass	|	Displays "fatal: [%s -> %s]: FAILED! => %s" or "...ignoring"	|
|	v2_runner_on_file_diff	|		|	pass	|		|		|
|	v2_runner_on_no_hosts	|	runner_on_no_hosts	|	pass	|	pass	|		|
|	v2_runner_on_ok	|	runner_on_ok	|	Sets var host	|	pass	|	Displays "changed: [host_name]" or "ok: [host_name]"	|
|	v2_runner_on_skipped	|	runner_on_skipped	|	if showing skipped show skipped host	|	pass	|		|
|	v2_runner_on_unreachable	|	runner_on_unreachable	|	Sets var host	|	pass	|	Displays "fatal: [%s -> %s]: UNREACHABLE! => %s"	|
|	v2_runner_retry	|		|	pass	|		|	Displays "FAILED - RETRYING" task and retries left	|

## Playbooks methods ##										
|	v2 items	|	v1 items	|	initial defaults v2	|	initial defaults v1	|	Default callback Plugin	|
|	-------------	|	-------------	|	-------------	|	-------------	|	-------------	|
|	v2_playbook_on_cleanup_task_start	|		|	pass	|		|	Display "CLEANUP TASK [task_name]"	|
|	v2_playbook_on_handler_task_start	|		|	pass	|		|	Display "RUNNING HANDLER [handler_task_name]"	|
|	v2_playbook_on_import_for_host	|	playbook_on_import_for_host	|	Sets var host	|	pass	|		|
|	v2_playbook_on_include	|		|	pass	|		|	Display 'included: %s for %s'	|
|	v2_playbook_on_no_hosts_matched	|	playbook_on_no_hosts_matched	|	pass	|	pass	|	Display "skipping: no hosts matched"	|
|	v2_playbook_on_no_hosts_remaining	|	playbook_on_no_hosts_remaining	|	pass	|	pass	|	Display "NO MORE HOSTS LEFT"	|
|	v2_playbook_on_not_import_for_host	|	playbook_on_not_import_for_host	|	Sets var host	|	pass	|		|
|	v2_playbook_on_notify	|	playbook_on_notify	|	Sets var host	|	pass	|		|
|	v2_playbook_on_play_start	|	playbook_on_play_start	|	pass	|	pass	|	Displays play name	|
|	v2_playbook_on_setup	|	playbook_on_setup	|	pass	|	pass	|	Displays "skipping: [host_name] => (item=%s) "	|
|	v2_playbook_on_start	|	playbook_on_start	|	pass	|	pass	|	Displays playbook and verbosity level	|
|	v2_playbook_on_stats	|	playbook_on_stats	|	pass	|	pass	|	Displays "PLAY RECAP" and host summary	|
|	v2_playbook_on_task_start	|	playbook_on_task_start	|	pass	|	pass	|	Displays the task via print task banner	|
|	v2_playbook_on_vars_prompt	|	playbook_on_vars_prompt	|	pass	|	pass	|		|

## Misc methods ##										
|	v2 items	|	v1 items	|	initial defaults v2	|	initial defaults v1	|	Default callback Plugin	|
|	-------------	|	-------------	|	-------------	|	-------------	|	-------------	|
|		|	\__init\__	|		|	sets options, display, etc	|	Sets vars self._play, self._last_task_banner to None	|
|		|	_clean_results	|		|	removes data from results for display	|		|
|		|	_dump_results	|		|	indents results, Removes base keys, exepction. Removes invocation and diff in result when less than level 3 verbosity. Returns json	|		|
|		|	_get_diff	|		|	Returns differences	|		|
|		|	_get_item	|		|	Sets var item	|		|
|		|	_handle_exception	|		|	Displays exeption occured, and if Verbosity 3 shows traceback	|		|
|		|	_handle_warnings	|		|	Displays 'warnings and depreciations	|		|
|		|	_process_items	|		|	Del items, now handeled by individual callbacks	|		|
|	v2_on_any	|	on_any	|	pass	|	pass	|		|
|	v2_on_file_diff	|	on_file_diff	|	Sets var host	|	pass	|	shows diff on file changed	|
|		|	set_options	|		|	Sets options, default is none	|		|
|		|	set_play_context	|		|	pass	|		|
|	Within default Callback module only	|	_print_task_banner	|		|		|	Displays task	|
                    
