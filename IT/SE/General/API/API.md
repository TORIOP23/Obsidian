## REST
- Example: `GET https://api.github.com/users/{username}/repos`
## [[GraphQL]]
- `https://api.example.com/graphql`
## SOAP
- `https://api.example.com/soap`
- Request & response is XML
```XML
request
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <TransferFunds xmlns="http://bank.example.com/">
      <FromAccount>12345</FromAccount>
      <ToAccount>67890</ToAccount>
      <Amount>100</Amount>
    </TransferFunds>
  </soap:Body>
</soap:Envelope>

```
## WebSocket
- `wss://api.example.com/chat`
## gRPC
