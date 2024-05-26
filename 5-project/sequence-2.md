```mermaid
sequenceDiagram
autonumber
    actor T as Tutor
    participant W as Web App
    participant P as Passport
    participant G as Gateway
    participant U as Users service
    participant A as Activity service
    participant Ts as Tasks service
    critical Authenticating 
    T ->>+ W: Authenticate
    W ->>+ P: Check credentials
    P -->>- W: Return result
    option authenticated
        W-->>T: Show personal account
    option rejected
        W-->>T: Access not allowed
    end
    T ->> W: Select student
    W ->>+ G: Find student
    G ->>+ U: Find student's info
    G ->>+ A: Find student's activities
    G ->>+ Ts: Find student's tasks
    U -->>- G: Return result
    A -->>- G: Return result
    Ts -->>- G: Return result
    G -->>- W: Return result
    W -->> T: Show student page
```