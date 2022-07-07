# Pushover bash script

Send notifications via Pushover.

## Message priorities

|    |                                                                                                       |
|----|-------------------------------------------------------------------------------------------------------|
| -2 | Lowest priority. No sound or vibration, and doesn't generate a notification (badge # increase on iOS) |
| -1 | Low priority. No sound or vibration, but will generate a notification.                                |
| 0  | Default. During quiet hours messages are sent as low priority.                                        |
| 1  | High priority. Bypasses quiet hours.                                                                  |
| 2  | Emergency. Same as high priority, but will repeat until notification is acknowledged.                 |

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


