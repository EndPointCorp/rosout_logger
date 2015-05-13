# ROS to syslog bridge

Configurable ROS ([Robot Operating System](http://www.ros.org/)) logger
that acts as a bridge between /rosout_agg and local or remote syslog daemon.

By default it will log to local7 facility

## Configuration parameters (rosparam)

Basic rosparams:

- syslog_facility - `local7` by default (string)
- ros_log_source - `/rosout_agg` by default (string)
- respect_severity - tells whether ROS logger should translate ros `level` to syslog `severity` - by default set to `true` (bool)
- log_host - host of a syslog daemon that logs should be submitted to
- log_port - udp port of a syslog daemon that logs should be submitted to

Following rosparams tell whether to include specific fields in log
entries (all fields are enabled by default):

- include_seq (bool)
- include_ros_node_name (bool)
- include_file_name (bool)
- include_function_name (bool)
- include_line (bool)
- include_topic (bool)

## Example log file entry

```
2015-05-11T19:03:41-04:00 localhost seq ros_node file function line (topic1,
topic2)  A `seq`'th message generated by a `function` implemented in `line` in a
`file` of a `ros_node` that interacted with `topic1` and `topic2`
```