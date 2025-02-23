Solaris-server is a centralized monolithic message bus that delegates tasks between administrators and agents. 

## Schema

```json
{
  "ec": "EVENT_CODE",              
  "d": {                       
    // Data is dependent on event
  },
  "e": "EVENT_NAME"  // Event Name
}
```

- Event code is the code that the event is supposed to interpret.
- Data is the information available to the event.
- Event name is the event handler for the server to delegate to.

### Example 

```json
{
  "ec": 0,
  "d": {
    "file_name": "image.png",
    "chunk_index": 1,
    "total_chunks": 5,
    "chunk_data": "<base64_encoded_chunk>",
    "checksum": "abcd1234"
  },
  "e": "UPLOAD"
}
```

## Version Control

- Server hosts binaries and setup files for both platforms and all versions.
- 
