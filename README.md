cmail runs a command and sends the output to your email address at certain 
intervals.

The main purpose of cmail is to track long running commands with periodic
email updates.

Assuming you have [GOPATH setup](http://golang.org/doc/code.html#GOPATH), cmail 
can be installed with

```bash
go get github.com/BurntSushi/cmail
```

## Usage
Either `-to` or an environment variable `$EMAIL` *must* be set to the email
address to send mail to.

Use the `-sendmail` and `-subj` options to match your preferences and
environment. (The sendmail command is invoked with `cmd -t` and given the
email body/headers on stdin.)


```
Usage: cmail [flags] [command [args]]

cmail sends data read from `command` periodically, and/or
when EOF is reached. If no command is given, data is read from stdin.

-inc (default: false)
    If set, emails will contain incremental changes as opposed to
    each email containing all data. Will also use less memory.
-no-pass (default: false)
    If set, stdout/stderr will not be passed thru.
-no-period (default: false)
    If set, only one email will be sent when the command finishes.
-period (default: 1h)
    The amount of time to wait between sending data gathered from
    stdin. Value should be a duration defined by Go's
    time.ParseDuration. e.g., '300ms', '1.5h', '1m'.
-sendmail (default: msmtp)
    The command to use to send mail. The email content and headers
    will be sent to stdin.
-subj (default: [cmail] )
    A subject prefix to use for all emails.
-to
    The email address to send mail to. By default, this is set to the
    value of the $EMAIL environment variable.
```

