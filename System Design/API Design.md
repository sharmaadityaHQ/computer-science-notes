## API Design basics

- Proper naming. Action that we are doing should define the name and the parameters. Avoid extra parameters.

- Additional parameters can be allowed if you need to give your service more information so that it does not have to make network calls to other services. This is usually done to speed up the API.

- Response object defining. Building a bigger response to make it extensible for future is a bad idea. Do not give more information than the caller needs (more network requirement).

- Think of common expectations and responsibilities your API has when designing errors.

- No side effects (doing everything in 1 function). Atomicity (entire transaction takes place at once or does not happen at all). (Transaction is a logical unit of work which accesses and possibly modifies the contents of a database) The problem of atomicity can be solved by calling the right actions instead of calling a more generic one.

- Break response into pieces if it is too large. (Pagination or Fragmentation (Say the response is more than 10KB then break it into multiple pieces and give it to the next service))

- Analyze how much consistency is needed. Cache is present or not?

- Response size can be reduced if load on database is high. This is service degradation where only essentials are sent in response, without completely crashing the API.