# check_rabbitmq

## Overview
Needed a simple way to check rabbitmq for connection and queue counts.  This was the quick dirty solution.
Posting as it might be useful for others and a nice beginning for a fuller featured plugin.

## Installation
Just drop it in your NRPE or Nagios libexec directory.

## Usage

We used this with NRPE on the server where rabbitmq was doing it's thing.
Here's an example from our nrpe.cfg

<pre><code>
command[rab_connection_count]=/cloud/src/server/nagios/nrpe64/libexec/check_rabbitmq -a connection_count -C 100 -W 80
command[rab_queries_count]=/cloud/src/server/nagios/nrpe64/libexec/check_rabbitmq -a queues_count -C 100 -W 80
</code></pre>

## DC Specific Usage

This runs on the queue servers. The easiest way to debug or add to this is to SSH to the server and modify it there.

You can either pull this repo and run it from your home directory, or the nagios plugin install location.

```
./check_rabbitmq -a queues_count --queuename email_park_to_friend_queue -C 5 -W 1
```

## License
Copyright (c) Nick Thuesen

* [GPLv3](http://www.gnu.org/copyleft/gpl.html)
