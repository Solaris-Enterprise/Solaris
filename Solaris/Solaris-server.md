Solaris-server is a centralized monolithic message bus that delegates tasks between administrators and agents. 
## Schema

```json
{
  "op": <opcode>,              
  "d": {                       
    # Data is dependent on event
  }
  "t": "EVENT_NAME" # Event Name
}
```

- op is the opcode that is tied to the event.
- d is the data, also dependent on the event.
- t is the event in question.

### Example 

```json
{
  "op": 0,
  "d": {
    "file_name": "image.png",
    "chunk_index": 1,
    "total_chunks": 5,
    "chunk_data": "<base64_encoded_chunk>",
    "checksum": "abcd1234"
  },
  "t": "UPLOAD"
}
```
