# Errors

The Peach API uses the following error codes:

Error Code | ID                              | Description
-----------|---------------------------------|------------
`400`      | `BAD_REQUEST`                   | Your request is invalid.
`400`      | `FORM_INVALID`                  | The form data is invalid.
`400`      | `TRANSACTION_INVALID`           | The transaction is invalid.
`401`      | `UNAUTHORIZED`                  | Unauthorized access.
`404`      | `NOT_FOUND`                     | The requested resource was not found.
`409`      | `DUPLICATE`                     | Duplicate resource found.
`429`      | `TOO_MANY_REQUESTS`             | Too many requests.
`500`      | `INTERNAL_SERVER_ERROR`         | Internal server error.
`503`      | `SERVICE_UNAVAILABLE`           | The service is currently unavailable.