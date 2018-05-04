# Reference for Ansible Callback Modules #


## Methods for Ansible Callback class ##
The following code snippet returns all of the methods of the Callback Class
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
