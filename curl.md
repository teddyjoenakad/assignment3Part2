# Curl commands for testing the server

## Testing the frontend

```bash
curl http://146.190.3.198
```

## Testing the backend

```bash
curl http://146.190.3.198/hey
```

```bash
curl -X POST -H "Content-Type: application/json" \
  -d '{"message": "Hello from your server"}' \
  http://146.190.3.198/echo
```
