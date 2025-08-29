---
include: "*.py"
title: HTTP conventions in API endpoints
tags: python,flask,quart
---

Ensure that for any new endpoint, the status code is matched with the correct purpose:

- Use `401 Unauthorized` for authentication failures (when credentials are missing or invalid)
- Use `403 Forbidden` for authorization failures (when user is authenticated but lacks required permissions)
- Use `404 Not Found` for resources that don't exist
- Use `400 Bad Request` for invalid request parameters
- Use `500 Internal Server Error` for server-side errors

Bad:

```python
# Wrong status code for permission error
@app.route('/resource')
def get_resource():
    if not user.is_authenticated:
        return jsonify({"error": "Permission denied"}), 401
    if not user.has_permission('read_resource'):
        return jsonify({"error": "Permission denied"}), 401  # Wrong code
    # ...
```

Good:

```python
# Correct status codes for different scenarios
@app.route('/resource')
def get_resource():
    if not user.is_authenticated:
        return jsonify({"error": "Authentication required"}), 401
    if not user.has_permission('read_resource'):
        return jsonify({"error": "Permission denied"}), 403  # Correct code
    # ...
```
