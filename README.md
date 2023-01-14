# Extract messages from a local Microsoft Teams installation.

This tool can be used to extract the Messages (and some other useful content) from a local Teams installation. It requires no extra privileges or access to any server, since it just accesses your local Teams "cache".

## Example Usage
```
python3 utils/dump_leveldb.py -o teams.json -f .../Application\ Support/Microsoft/Teams/IndexedDB/https_teams.microsoft.com_0.indexeddb.leveldb
./decode_teams.py teams.json
```
## Description

The first command reads & parses the teams "cache" levelDB.
You need to specify the full path to that directory. It's location may vary depending on your OS, but dhe directory in question should always be called `https_teams.microsoft.com_0.indexeddb.leveldb`.

It's output will be a file called `teams.json` with all the decoded contents in machine readable form.

The second command will read the `teams.json` and convert it into human readable files in the specified output directory (defaults to `conversations/`).

The output consists of one file per Chat/Meeting/Space/Topic you participate in, which should contain a human readable plaintext version of your conversations.

You may also get a `Thread_*` file which contains a log of all your recent calls and a `Conversation_*` file which will contain a log of all recent notifications sent to you.

## References

Original work on parsing the LevelDB files from
https://github.com/cclgroupltd/ccl_chrome_indexeddb
and
https://github.com/lxndrblz/forensicsim.git
