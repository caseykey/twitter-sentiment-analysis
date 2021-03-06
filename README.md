# Twitter Sentiment Analyzer

This is a Python library for identifying sentiment of different topics live from Twitter.

Twitter does not allow streaming from multiple tracks. 
This tool allows you to group a wide stream of tweets with labels.
These Tweets are analyzed and their 'mood' is determined using an amalgam of algorithms. 

## Usage
First create a twitter-creds.json file with your keys and tokens from a [Twitter Developer] app.
```json
{
    "CONSUMER_KEY": "apikeyhere123456abcdefgh",
    "CONSUMER_SECRET": "consumersecrethere123456789abcdefghijklmnopqrstuv",
    "ACCESS_KEY": "accesskeyhereaccesskeyhereaccesskeyhereaccesskey1",
    "ACCESS_SECRET": "accesssecrethereaccesssecrethereaccesssecret12"
}  
```

For Autonomous Database support, follow [these](https://cx-oracle.readthedocs.io/en/latest/installation.html#installing-cx-oracle-on-macos) intructions:
1. Install the cx_Oracle Python package 
2. Install Oracle Instant Client
3. Set environment variables to locate the tnsnames.ora file

Something like this:
```bash
export LD_LIBRARY_PATH=/usr/lib/oracle/18.3/client64/lib/${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
``` 

### General Usage 
To enter a custom search query and save tweets to output.txt,
execute these commands from a shell:
```bash
git clone https://github.com/caseykey/flock
cd flock
python3 flock.py output.txt
```
Ctrl-C to exit the process.
To continue the previous search contained in query.txt, execute:
```bash
python3 flock.py output.txt go
```
### As a Python Module
General streaming usage:
```python
from flock import Flock

# save tweets to output.txt using previous search terms
stream = Flock(json_creds='api_creds.json', output='output.txt', cont='go')
stream.start(quiet=False) # begin reading tweets
```

To fetch historical tweets, use:
```python
from flock import Flock

# save tweets to output.txt using previous search terms
stream = Flock(json_creds='api_creds.json', output='output.txt', cont='go')
'''
Change fetch's cont argument to True if you want to continue a from
the date of the last tweet in an existing file.
'''
stream.fetch(cont=False)
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)


