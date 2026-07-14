| Code    | Meaning                   | Problem                                       |
| ------- | ------------------------- | --------------------------------------------- |
| 200     | OK                        | Everything worked                             |
| 201     | Created                   | Resource created successfully                 |
| 400     | Bad Request               | Invalid request from client                   |
| 401     | Unauthorized              | Authentication required                       |
| 403     | Forbidden                 | Access denied                                 |
| 404     | Not Found                 | Resource doesn't exist                        |
| 405     | Method Not Allowed        | HTTP method not allowed                       |
| **500** | **Internal Server Error** | **Application crashed or threw an exception** |
| 502     | Bad Gateway               | Reverse proxy couldn't reach backend          |
| 503     | Service Unavailable       | Service is down or overloaded                 |
| 504     | Gateway Timeout           | Backend took too long to respond              |
