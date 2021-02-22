# Role of a variable
**Variable has multiple purposes (logic less obvious) => easier to introduce bugs**
- Constant/Fixed Value  
  **Initialized without any calculation**  
  **Does not change thereafter**
- Stepper  
  **Stepping through values**  
  **Can be predicted**
- Most-recent holder (hold latest value)
- Gatherer (accumulator)
- One-way flag (boolean)
- Temporary (Holding very short period)
- Organizer  
  **Rearrange element after initialization**  
  **e.g list, array**
- Transformation (Gets new value with same calculation from another variable)

# Use Case
## Diagram
**Use simple grammar**  
**Any step should lead to some progress**
- Finding actors  
  **Human/System interact with main system outside**  
  **Provide input or take output from system**
  **Role and objective**
  - Primary (interact directly with system)
  - Secondary  
    **Interact indirectly with system**  
    **Support and complete the use case with primary actor**
  - <\<include\>>  
    **Must be executed**  
    **Can extract partial function as a new use case if multiple use case needs that function**  
    **May not exist independently**  
    ![Include](Image/use-case-include.png)
  - <\<extend\>>  
    **Optional behavior with condition**  
    **Can separate independently**  
    ![Extend](Image/use-case-extend.png)
  - Generalization actor/use case (Inheritance)
  - Description  
    **<\<include\>> Invoke the use case XXXXX**  
    **<\<extend\>> \[Extension point: (condition), invoke XXXXX\]**

    | Field | Content |
    | --- | --- |
    | Use Case Name | Name of the use case |
    | Actor(s) | List the actors who can perform this use case |
    | Description | State clearly the purpose of the use case |
    | Reference ID | ID of use case |
    | Precondition | Describe the state of the system before the use case |
    | Postcondition | State of the system in following completion |
    | Flow of events | Interaction steps between actors and the system - actor action/system response |
    | Alternative flow of events | if any |
    | Exceptions | if any |
    | Assumptions | if any |
## Benefits
- Define the scope of the system 
- Plan the development process 
- Develop and validate the requirements 
- Form the basis for the definition of test cases 
- Structure user manuals 
