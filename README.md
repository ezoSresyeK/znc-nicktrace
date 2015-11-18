# znc-nicktrace
A ZNC module to track users

## Requirements
 * <a href="http://znc.in">ZNC</a>
 * <a href="https://www.python.org">Python 3</a>
 * <a href="http://wiki.znc.in/Modpython">modpython</a>
 * <a href="http://docs.python-requests.org/en/latest/">python3-requests</a>
 * <a href="https://www.sqlite.org">sqlite3</a>

## Installation
To install aka, place aka.py in your ZNC modules folder

## Loading
aka must be loaded on each network you wish to use it on
`/msg *status loadmod Aka`

## Commands

### Aggregate Commands

`all nick <nick>` Perform complete lookup on nick (trace, channels, offenses, geoip, seen)

`all host <host>` Perform complete lookup on host (trace, channels, offenses, geoip, seen)

### `trace` Commands

`nick <nick>` Shows nick change and host history for given nick

`sharedchans nicks <nick1> <nick2> ... <nick#>` Show common channels between a list of nicks

`sharedchans hosts <host1> <host2> ... <host#>` Show common channels between a list of hosts

`intersect nicks <#channel1> <#channel2> ... <#channel#>` Display nicks common to a list of channels

`intersect hosts <#channel1> <#channel2> ... <#channel#>` Display hosts common to a list of channels

`channels nick <nick>` Get all channels a nick has been seen in

`channels host <host>` Get all channels a host has been seen in

### Moderation History Commands

`offenses nick <nick>` Display kick/ban/quiet history for nick

`offenses host <host>` Display kick/ban/quiet history for host

`offenses in nick <channel> <nick>` Display kick/ban/quiet history for nick in channel

`offenses in host <channel> <host>` Display kick/ban/quiet history for host in channel

### User Info Commands

`seen nick <nick>` Displays last time nick was seen speaking globally

`seen host <host>` Displays last time host was seen speaking globally

`seen in nick <#channel> <nick>` Displays last time nick was seen speaking in channel

`seen in host <#channel> <host>` Displays last time host was seen speaking in channel

`geoip <host>` Geolocates the given host

`geoip <nick>` Geolocates a user by nick

### Modify Data Commands

`add <nick> <host>` Manually add a nick/host entry to the database

`save` Manually save the latest tracks to disk

`import <url>` Imports user data to DB from valid JSON file url

`export nick <nick>` Exports nick data to JSON file

`export host <host>` Exports host data to JSON file

### Other Commands

`info` Display information about the module

`version` Get current module version

`getconfig` Print current network configuration

`config <variable> <value>` Set configuration variables

`stats` Print nick and host stats for the network

`update` Updates Aka to the newest version

`help` Print help from the module

## Configuration Variables

 * **DEBUG_MODE** *(True/False)* Display raw output
 * **NOTIFY_ON_JOIN** *(True/False)* Automatically run `trace nick` when a user joins a channel
 * **NOTIFY_ON_JOIN_TIMEOUT** *(int: seconds)* How long to wait before sending notification again for same user
 * **NOTIFY_DEFAULT_MODE** *(nick/host)* Whether to use nick or host for on join trace
 * **NOTIFY_ON_MODE** *(True/False)* Automatically be notified when channel modes are changed
 * **NOTIFY_ON_MODERATED** *(True/False)* Be notified when a user is banned, quieted, or kicked
 * **PROCESS_CHANNEL_ON_JOIN** *(True/False)* Process all users in a channel on join
 * **PROCESS_CHANNELS_ON_LOAD** *(True/False)* Process users in all channels when module is loaded

## Contact

Issues/bugs should be submitted on the <a href="https://github.com/emagaliff/znc-nicktrace/issues">GitHub issues page</a>.

For assistance, please PM MuffinMedic (Evan) on <a href="https://kiwiirc.com/client/irc.freenode.net:+6697">freenode<a/> or <a href="https://kiwiirc.com/client/irc.snoonet.org:+6697">Snoonet<a>.
