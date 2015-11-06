faire une signature d'un langage objet

code
1 demi page de tableau
1 demi page d'interprétation, analyse

# Late-binding semantics of the Matlab language

## Code

```matlab
% File Up.m
% definition of class Up
classdef Up
    methods
        function cv(obj, top)
            top;
            disp('Up');
        end
        function ctv(obj, bottom)
            bottom;
            disp('Up');
        end
    end
end

% File Down.m
% definition of class Down
classdef Down < Up
    methods
        function cv(obj, middle)
            middle;
            disp('Down');
        end
        function ctv(obj, middle)
            middle;
            disp('Down');
        end
    end
end

% File Top.m
% definition of class Top
classdef Top
end

% File Middle.m
% definition of class Middle
classdef Middle < Top
end

% File Bottom.m
% definition of class Bottom
classdef Bottom < Middle
end

% Test code
u = Up();
d = Down();
ud = Down(); %useless

% test for the Up class
u.cv(Top());
u.cv(Middle());
u.cv(Down());
u.ctv(Top());
u.ctv(Middle());
u.ctv(Down());

% test for the Down class
d.cv(Top());
d.cv(Middle());
d.cv(Down());
d.ctv(Top());
d.ctv(Middle());
d.ctv(Down());

% same as the Down class
ud.cv(Top());
ud.cv(Middle());
ud.cv(Down());
ud.ctv(Top());
ud.ctv(Middle());
ud.ctv(Down());
```

Result :

|             | u   | d    | ud   |
|-------------|-----|------|------|
| cv(Top)     | Up  | Down | Down |
| ---         | --- | ---  | ---  |
| cv(Middle)  | Up  | Down | Down |
| ---         | --- | ---  | ---  |
| cv(Bottom)  | Up  | Down | Down |
| ---         | --- | ---  | ---  |
| ctv(Top)    | Up  | Down | Down |
| ---         | --- | ---  | ---  |
| ctv(Middle) | Up  | Down | Down |
| ---         | --- | ---  | ---  |
| ctv(Bottom) | Up  | Down | Down |
| ---         | --- | ---  | ---  |

# late binding for F#

## Code

```{.cpp}
int main(void)
{
  return 0;
}
```

```fsharp
type Top () =
    abstract member F : unit -> unit
    default u.F() =
        printfn "F Top"

type Middle () =
    inherit Top()
    override u.F() =
        printfn "F Middle"
    
type Bottom () =
    inherit Middle()
    override u.F() =
        printfn "F Bottom"

type Up ()=
    member this.cv (myTop : Top) =
        printfn "Up"
    member this.ctv (myBottom : Bottom) =
        printfn "Up"

type Down ()=
    inherit Up()
    member this.cv (myMiddle : Middle) =
        printfn "Down"
    member this.ctv (myMiddle : Middle) =
        printfn "Down"
 
let u = Up()
let d = Down()
let ud : Up = Down() :> Up

printfn("testing u")
// doing ascending casting to use the cv method of class Up
u.cv(Top())
u.cv(Middle())
u.cv(Bottom())

//can't do descending casting to use the ctv method of class Up
//u.ctv(Top())
printfn("error for u.ctv(Top())")
//u.ctv(Middle())
printfn("error for u.ctv(Middle())")
u.ctv(Bottom())

printfn("testing d")
//use the method of the mother class Up
//because signature is better
d.cv(Top())
//use the method of the daughter class Down
d.cv(Middle())
//use the method of the daughter class Down with ascending casting
d.cv(Bottom())

//can't do a descending cast from an object Top to object Middle or Bottom
//d.ctv(Top())
printfn("error for d.ctv(Top())")
//using method from daughter class
d.ctv(Middle())
//using method from mother class because better signature
d.ctv(Bottom())

printfn("testing ud")
//same comportement as a pure Up object
//the ascending cast is shadowing the Down part of the object
ud.cv(Top())
ud.cv(Middle())
ud.cv(Bottom())

//ud.ctv(Top())
printfn("error for ud.ctv(Top())")
//ud.ctv(Middle())
printfn("error for ud.ctv(Middle())")
ud.ctv(Bottom())
```

|               | u     | d      | ud     |
| ------------- | ----- | ------ | ------ |
| cv(Top)       | Up    | Down   | Down   |
| ---           | ---   | ---    | ---    |
| cv(Middle)    | Up    | Down   | Down   |
| ---           | ---   | ---    | ---    |
| cv(Bottom)    | Up    | Down   | Down   |
| ---           | ---   | ---    | ---    |
| ctv(Top)      | Up    | Down   | Down   |
| ---           | ---   | ---    | ---    |
| ctv(Middle)   | Up    | Down   | Down   |
| ---           | ---   | ---    | ---    |
| ctv(Bottom)   | Up    | Down   | Down   |
| ---           | ---   | ---    | ---    |

