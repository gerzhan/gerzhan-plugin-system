# 01. Общее описание

> Общая (вводная) информация о проекте(ах) репозитория

Репозиторий содержит демонстрационный пример/заготовку приложения/системы с подгружаемыми плагинами

```plantuml
left to right direction

rectangle Application {
component "System Core (cli)" as SystemCore
component "Plugin Manager" as PluginManager
component "System Service (Payment f())" as SystemService
'--взаимодействие в приложении
SystemCore <-down-> PluginManager
PluginManager <-down-> SystemService
}


rectangle Plugins {
  component  "Plugin (Payment Type N1)" as PluginPayment.N1
  component  "Plugin (Payment Type N2)" as PluginPayment.N2
'-- оформление отображения
PluginPayment.N1 -[hidden]- PluginPayment.N2
}
'-- оформление
Application -[hidden]- Plugins

'-- взаимодействие между Application и Plugins
SystemService .- PluginPayment.N1
SystemService .- PluginPayment.N2

PluginPayment.N1 -[hidden]- SystemService
PluginPayment.N2 -[hidden]- SystemService

PluginManager -> PluginPayment.N1
PluginManager -> PluginPayment.N2
```
