# audd
<a href="./LICENSE.md"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>

Record audio and use the [AudD](https://audd.io) music recognition API from the command line.

The `[audd](./audd)` scripts queries the AudD API. This repository also contains `[audd-notif](./audd-notif)` which uses `[audd](./audd)` and `libnotify` to return the match result.

## Dependencies:
The `audd` script requires:
* [curl](https://github.com/curl/curl)
* [ffmpeg](https://git.ffmpeg.org/ffmpeg.git)

In addition to the above the `audd-notif` script requires:
* [jq](https://github.com/stedolan/jq)
* notify-send
* [dunstify](https://github.com/dunst-project/dunst) (optional)

## Installation

tba

## Usage
```sh
$ audd -h
Usage: audd [OPTION]... [FILE]
Query the AudD music recognition API.

Get a free API token at: https://audd.io/

The API token can be read from file:
$ echo "api-token" > "/home/lcoyle/.config/audd/api_token"

If no FILE is provided, a recording is made using the AUDIO_SOURCE.

Usage:
    -h                    Show this message and exit.
    -a API_KEY            AudD API token.
    -s AUDIO_SOURCE       ffmpeg audio input source, (default: "default").
    -t RECORDING_TIME     Length of recording time, in seconds, (default: 3).
    -r API_RETURN         AudD API return parameter, see https://docs.audd.io/,
                          (default: "apple_music,spotify").
    -o                    Use the "recognizeWithOffset" endpoint.
```

To use `audd` you will need to get an API key from [audd]([https://audd.io).
Provide the API key with either the `-a` option or by writing the API key to `${XDG_CONFIG_HOME:-$HOME/.config}/audd/api_token`:

```sh
$ echo "api-token" > "/home/lcoyle/.config/audd/api_token"
```

`audd` can perform a query using an audio file (the file shouldn't be too large, typically shorter than 20 seconds), or if no file is provided. it will record an audio sample from the provided audio source, with the `-s` option.

I recommend reading the [API docs](https://docs.audd.io/) to understand the `-r` and the `-o` options.
