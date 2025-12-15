## Shapes ##
((Circle)) - Used for start/end  
Often means initialisation, entry point, or setup phase  
{{Hexagon}} - Represents a preparation step  

Syntax	Shape	Typical meaning  
( )	Rounded	Process  
(( ))	Circle	Start / End  
[ ]	Rectangle	Action  
{ }	Diamond	Decision  
{{ }}	Hexagon	Preparation / Build  
[/ /]	Parallelogram	Input / Output  
[()]	Database	Data

```mermaid
 flowchart TB
    subgraph AWS["AWS Account"]
        Lambda
 rounded((rounded))
 startorend((start))
        DB[(RDS)]
    end
    subgraph External["systemx"]
        API[3rd-party API]
        Hex{{Hexagon}}
        DiamondDecision{Decision}	 
    end
  

    subgraph External["External Systems"]
        Database[(DB)]
InputorOutput[/Parallelogram/]
    end
```
