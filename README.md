# Custom Error Exceptions

[![Test Status](https://camo.githubusercontent.com/2794f4681fea92b30572a3c51d1d0e59458bd291/68747470733a2f2f696d672e736869656c64732e696f2f636f766572616c6c732f657870726573736a732f657870726573732f6d61737465722e737667)](https://github.com/brothergiez/custom-error-exceptions/) 

Custom error exceptions are made to make it easier to handling errors. You can also make custom errors as needed.

# Installation

```sh
$ npm install custom-error-exceptions
```

# Usage
**Using Template Error (BAD_REQUEST)**
```javascript
const express = require('express');
const {
  handlers: { errorHandler },
  errors: { BadRequestError }
} = require('custom-error-exceptions');

const app = express();
const port = 3044;
app.use(express.json());

//TEMPLATE BAD REQUEST ERROR 
app.post('/', (req, res) => {
  const name = req.body.name;
  if (typeof name !== 'string') {
    throw new BadRequestError();
  }
  res.send(
    req.body
  );
});

//Error Handler
app.use(errorHandler);
app.listen(port, () => console.log(`app listen on port ${port}`));
```

**Using Template Error (BAD_REQUEST) With Custom Message**

```javascript
//TEMPLATE BAD REQUEST ERROR WITH CUSTOM MESSAGE
app.post('/custom-message', (req, res) => {
  const name = req.body.name;
  if (typeof name !== 'string') {
    throw new BadRequestError('Name type must be string');
  }
  res.send(req.body);
});
```

**Using Custom Error**
```javascript
const {
  handlers: { errorHandler },
  errors: { CustomError }
} = require('custom-error-exceptions');

//CUSTOM ERROR
app.post('/custom-error', (req, res) => {
  const name = req.body.name;
  if (typeof name !== 'string') {
    throw new CustomError('Custom Message', 'CUSTOM_CODE', 700);
  }
  res.send(req.body);
});
```

**Handling NOT_FOUND Route**
```javascript
const {
  handlers: { errorHandler, notFoundHandler },
} = require('custom-error-exceptions');

------------------------------------
             YOUR ROUTE
------------------------------------

app.use(notFoundHandler);
app.use(errorHandler);
```

To further explore you can see an [example][example] this repo.

# LIST OF ERROR TEMPLATES
* CustomError
* BadRequestError
* UnauthorizedError
* PaymentRequiredError
* ForbiddenError
* NotFoundError
* MethodNotAllowedError
* NotAcceptableError
* ProxyAuthenticationError
* RequestTimeoutError
* ConflictError
* GoneError
* LengthRequiredError
* PreconditionFailedError
* PayloadTooLargeError
* UriTooLongError
* UnsupportedMediaTypeError
* RangeNotSatisfiableError
* MisdirectedRequestError
* UnprocessableEntityError
* LockedError
* FailedDependencyError
* TooEarlyError
* UpgradeRequiredError
* PreconditionRequiredError
* TooManyRequestsError
* RequestHeaderError
* LegalReasonsError
* InternalServerError
* NotImplementedError
* BadGatewayError
* ServiceUnavailableError
* GatewayTimeoutError
* HttpNotSupportedError
* VariantAlsoNegotiatesError
* InsufficientStorageError
* LoopDetectedError
* NotExtendedError
* NetworkAuthenticationRequiredError

The list above is based on the client error list and server error list as on this [page][page].

# Author
* Cristoph Adam Sugianto [@brothergiez][@brothergiez]

[example]: <https://github.com/brothergiez/custom-error-exceptions/blob/master/example/src/index.js>
[page]: <https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_Client_errors>
[@brothergiez]: <https://github.com/brothergiez>