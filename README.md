## Validation middleware for express with joi library
This is easy to use simple validator middleware for express routes.
No need to validate input parameters manually, just configure route middleware.
Uses Joi library:
https://github.com/hapijs/joi

### Install with npm
```
  npm install express-joi-params
```

### Use

In your express route file include

```
const validation = require('express-joi-params');
const rule = require('./validation').rule;
```
then in any rote add middleware

```
router.post('/api/login', validation.validateRequest({
  body: {
    login: rule.string().required(),
    password: rule.string().required(),
  },
}), authController.login);
```

in case of error will output
```
{
    "message": "Some parameters are missing or invalid",
    "success": false,
    "errors": {
        "errors": [
            {
                "message": "\"username\" is required",
                "type": "any.required",
                "field": [
                    "username"
                ]
            }
        ],
        "type": "body"
    }
}
```
also will give 400 http code and will stop execution


## [MIT License](https://github.com/georgearrowwood/resize-to-s3/blob/master/LICENSE)