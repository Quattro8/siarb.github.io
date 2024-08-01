# Perch&#233; questo libro?

## UML

```plantuml
@startuml

hide empty members
hide circle

package Configuration <<Rectangle>> {
interface RunProfile
interface RunConfiguration
interface RunProfileState
}

package Execution <<Rectangle>> {
abstract class Executor
interface ProgramRunner
class ExecutionEnvironment
class RunContentBuilder
abstract class ExecutionResult
interface ExecutionConsole
abstract class ProcessHandler
}

RunProfile <|.. RunConfiguration
RunProfile --> RunProfileState: creates

RunProfileState --> ExecutionResult: prepares

ExecutionResult o-- "1" ExecutionConsole
ExecutionResult o-- "1" ProcessHandler

ProgramRunner --> RunProfile: executes
ProgramRunner --> Executor
ProgramRunner --> ExecutionEnvironment
ProgramRunner -r-> RunContentBuilder

@enduml
```


