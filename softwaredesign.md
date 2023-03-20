
## Software Architecture
https://github.com/jasontaylordev/CleanArchitecture 

![Clean Architecture](./img/clean-architecture.png)

## Code Smells
&nbsp; |  &nbsp;
-- | --
Large Class | Extract Class <br/> Extract Subclass <br/> Extract Interface
Long Method | Replace Method with Method Object <br/> Compose Method <br/> Extract Method <br/> Move Method



#### Core project
- Interfaces
- Aggregates 
    - Entities
- Value Objects
- Domain Services
- Domain Exception


- Domain Events, Events Handlers
- Specifications
- Validators
- Enums
- Custom Guards

Shared Kernel