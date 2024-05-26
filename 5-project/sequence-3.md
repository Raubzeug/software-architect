```mermaid
sequenceDiagram
autonumber
    actor T as User
    participant W as Web App
    participant P as Passport
    participant G as Gateway
    participant R as Report sercice
    participant N as Notify sercice
    critical Authenticating 
    T ->>+ W: Authenticate
    W ->>+ P: Check credentials
    P -->>- W: Return result
    option authenticated
        W-->>T: Show personal account
    option rejected
        W-->>T: Access not allowed
    end
    T ->> W: Select report
    W ->>+ G: Report query
    G ->>+ R: Get report
    R ->> R: Calculations
    R ->>- N: Report is ready
    N -->> W: Report is ready
    W -->> T: Show link to report 
```