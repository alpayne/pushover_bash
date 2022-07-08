# Pushover bash script

This script send notifications via Pushover. It's 200 lines of wrapper code around a call to `curl`.

See the [Pushover API documentation](https://pushover.net/api) for details on each of the parameters. Most are also described in the same config file.

## Message priorities

|    |                                                                                                       |
|----|-------------------------------------------------------------------------------------------------------|
| -2 | Lowest priority. No sound or vibration, and doesn't generate a notification (badge # increase on iOS) |
| -1 | Low priority. No sound or vibration, but will generate a notification.                                |
| 0  | Default. During quiet hours messages are sent as low priority.                                        |
| 1  | High priority. Bypasses quiet hours.                                                                  |
| 2  | Emergency. Same as high priority, but will repeat until notification is acknowledged.                 |

If sending an Emergency notificagtion, two additional parameters `retry` and `expire` can be provided. Retry is how often (in seconds) you want the message to be resent. Expiry is how long (in seconds) to keep retrying for. For example, sending a `retry` parameter of 60 and an `expire` parameter of 3600 will cause your notification to be retried every 60 seconds for 1 hour. 

## Usage

```text
  Usage: pushover [ --application <app_name> | --apptoken <token> ] --message <text> [ --config <config file> ] [ options ]

  Send a notification via Pushover.

  OPTIONS:
    -T --usertoken    User token
    -A --apptoken     Application token
    -a --application  Application name
    -m --message      Message (required)
    -t --title        Title of your notification
    -p --priority     Priority of your message : -2 (Silent), -1 (Quiet), 1 (High), 2 (Emergency)
    -s --sound        Sound (https://pushover.net/api#sounds)
    -i --image        Attach an image (up to 2.5mb)
    -u --url          URL Link
    -n --url_title    URL Title
    -r --retry        Retry (seconds)
    -e --expiry       Expiry (seconds)
    -d --device       Send to a specific device name
    -H --html         HTML Format

    Any of the above can be set in a config file.

    -c --config       Config file location (optional, use to set parameters for an app)
    -x --debug        Debug
    -h --help         Show this message

    Config file format, one per line:

      long_parameter="value"

    Application tokens can be stored in a hash table and called by application name with
    the --application parameter:

      app_tokens=(["application"]="token" ["application2"]="token2" ...)
```


